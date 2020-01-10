---
title: TN001：視窗類別註冊
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 95e35ddd6f55c955bc2adb7b4db2460ae84a6dc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513542"
---
# <a name="tn001-window-class-registration"></a>TN001：視窗類別註冊

此附注描述的 MFC 常式會註冊 Microsoft Windows 所需的特殊[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)。 討論`WNDCLASS` MFC 和 Windows 所使用的特定屬性。

## <a name="the-problem"></a>問題

[CWnd](../mfc/reference/cwnd-class.md)物件的屬性（例如`HWND` Windows 中的控制碼）會儲存在兩個位置： `WNDCLASS`視窗物件和。 `WNDCLASS`的名稱會傳遞至一般視窗建立功能，例如*lpszClassName*參數中的[CWnd：： create](../mfc/reference/cwnd-class.md#create)和[CFrameWnd：： create](../mfc/reference/cframewnd-class.md#create) 。

這`WNDCLASS`必須透過下列四種方式之一來註冊：

- 以隱含方式使用提供`WNDCLASS`的 MFC。

- 藉由子類別化 Windows 控制項（或其他控制項）來隱含。

- 藉由呼叫 MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)或[AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)來明確地進行。

- 藉由呼叫 Windows 常式[RegisterClass](/windows/win32/api/winuser/nf-winuser-registerclassw)來明確地進行。

## <a name="wndclass-fields"></a>WNDCLASS 欄位

`WNDCLASS`結構是由描述視窗類別的各種欄位所組成。 下表顯示欄位，並指定它們在 MFC 應用程式中的使用方式：

|欄位|描述|
|-----------|-----------------|
|*lpfnWndProc*|視窗處理器，必須是`AfxWndProc`|
|*cbClsExtra*|未使用（應為零）|
|*cbWndExtra*|未使用（應為零）|
|*hInstance*|自動填入[AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|框架視窗的圖示，請參閱下方|
|*hCursor*|當滑鼠停留在視窗上方時的游標，請參閱下方|
|*hbrBackground*|背景色彩，請參閱下方|
|*lpszMenuName*|未使用（應為 Null）|
|*lpszClassName*|類別名稱，請參閱下面的|

## <a name="provided-wndclasses"></a>提供的 WNDCLASSes

較早版本的 MFC （在 MFC 4.0 之前），提供數個預先定義的視窗類別。 預設不會再提供這些視窗類別。 應用程式應該`AfxRegisterWndClass`使用搭配適當的參數。

如果應用程式提供具有指定資源識別碼（例如，AFX_IDI_STD_FRAME）的資源，MFC 將會使用該資源。 否則，它會使用預設資源。 針對圖示，會使用標準應用程式圖示，而游標會使用標準箭號游標。

有兩個圖示支援具有單一檔案類型的 MDI 應用程式：一個主要應用程式的圖示，另一個是 iconic document/MDIChild 視窗的圖示。 針對具有不同圖示的多個檔案類型，您必須`WNDCLASS`註冊其他 es 或使用[CFrameWnd：： LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)函數。

`CFrameWnd::LoadFrame`會`WNDCLASS`使用您指定為第一個參數的圖示識別碼和下列標準屬性來註冊：

- 類別樣式：CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- 圖示 AFX_IDI_STD_FRAME

- 箭號游標

- COLOR_WINDOW 背景色彩

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)的背景色彩和游標的值不會使用，因為**MDICLIENT**視窗完全涵蓋的工作`CMDIFrameWnd`區。 Microsoft 不鼓勵將**MDICLIENT**視窗子類別化，因此盡可能使用標準色彩和游標類型。

## <a name="subclassing-and-superclassing-controls"></a>子類別化和 Superclassing 控制項

如果您將 windows 控制項（例如， [CButton](../mfc/reference/cbutton-class.md)）的子類別或超級類別化，則您`WNDCLASS`的類別會自動取得該控制項之 Windows 執行中提供的屬性。

## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 函式

MFC 提供一個 helper 函式來註冊視窗類別。 假設有一組屬性（視窗類別樣式、游標、背景筆刷和圖示），就會產生綜合名稱，並註冊產生的視窗類別。 例如，套用至物件的

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

此函式會傳回所產生之已註冊視窗類別名稱的暫存字串。 如需此函數的詳細資訊，請參閱[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)。

傳回的字串是靜態字串緩衝區的暫存指標。 在下一次呼叫`AfxRegisterWndClass`之前，它是有效的。 如果您想要保留此字串，請將它儲存在[CString](../atl-mfc-shared/using-cstring.md)變數中，如下列範例所示：

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass`如果視窗類別無法註冊（可能是因為參數不正確或超出 Windows 記憶體），將會擲回[CResourceException](../mfc/reference/cresourceexception-class.md) 。

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass 和 AfxRegisterClass 函式

如果您想要執行的動作比`AfxRegisterWndClass`提供的還複雜，可以呼叫 Windows API `RegisterClass`或 MFC 函數`AfxRegisterClass`。 `CWnd`、[CFrameWnd](../mfc/reference/cframewnd-class.md) 和[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)`Create`函式會將視窗類別的 *lpszClassName* 字串名稱當做第一個參數。 您可以使用任何已註冊的視窗類別名稱，不論您用來註冊它的方法為何。

請務必在 Win32 的`AfxRegisterClass` DLL 中`AfxRegisterWndClass`使用（或）。 Win32 不會自動取消註冊 DLL 所註冊的類別，因此您必須在 DLL 終止時明確地取消註冊類別。 藉由`AfxRegisterClass`使用`RegisterClass`而不是，系統會自動為您處理。 `AfxRegisterClass`維護由您的 DLL 註冊的唯一類別清單，並在 DLL 終止時自動將其取消註冊。 當您在`RegisterClass` dll 中使用時，您必須確定在 dll 終止時（在您的[DllMain](/windows/win32/Dlls/dllmain)函式中），所有類別都已取消註冊。 當另一個用戶端應用`RegisterClass`程式嘗試使用您的 DLL 時，無法執行此動作可能會導致意外失敗。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
