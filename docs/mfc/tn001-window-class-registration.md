---
title: "TN001： 視窗類別註冊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.registration
dev_langs:
- C++
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f4560905660ea80524c3e26bf14a803a2bc74344
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn001-window-class-registration"></a>TN001：視窗類別註冊
此提示描述註冊特殊的 MFC 常式[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)es 所需的 Microsoft Windows。 特定`WNDCLASS`討論 MFC 和 Windows 所使用的屬性。  
  
## <a name="the-problem"></a>問題  
 屬性的[CWnd](../mfc/reference/cwnd-class.md)物件，例如`HWND`處理在 Windows 中，會儲存在兩個地方： 視窗物件和`WNDCLASS`。 名稱`WNDCLASS`例如傳遞至一般視窗建立函式[cwnd:: Create](../mfc/reference/cwnd-class.md#create)和[CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create)中`lpszClassName`參數。  
  
 這`WNDCLASS`必須註冊到四個方法的其中一個：  
  
-   隱含地使用所提供的 MFC `WNDCLASS`。  
  
-   隱含地子類別化 Windows 控制項 （或一些其他控制項）。  
  
-   明確地呼叫 MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)或[AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)。  
  
-   明確地呼叫 Windows 常式[RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586)。  
  
## <a name="wndclass-fields"></a>WNDCLASS 欄位  
 `WNDCLASS`結構描述的視窗類別欄位所組成。 下表顯示的欄位，並指定在 MFC 應用程式的使用方式：  
  
|欄位|描述|  
|-----------|-----------------|  
|`lpfnWndProc`|視窗程序，必須是`AfxWndProc`|  
|`cbClsExtra`|不使用 （應為零）|  
|`cbWndExtra`|不使用 （應為零）|  
|`hInstance`|自動填滿[AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|  
|`hIcon`|框架視窗的圖示如下所示|  
|`hCursor`|資料指標，當滑鼠經過視窗中，請參閱下面的|  
|`hbrBackground`|背景色彩，請參閱下面|  
|`lpszMenuName`|不使用 （應為 NULL）|  
|`lpszClassName`|類別名稱，請參閱下面|  
  
## <a name="provided-wndclasses"></a>提供 WNDCLASSes  
 舊版的 MFC （之前 MFC 4.0)，提供數個預先定義的視窗類別。 預設不會再提供這些視窗類別。 應用程式應該使用`AfxRegisterWndClass`以適當的參數。  
  
 如果應用程式提供具有指定的資源識別碼 (例如，AFX_IDI_STD_FRAME) 的資源，MFC 會使用該資源。 否則它會使用預設的資源。 圖示，使用標準的應用程式圖示時，以及資料指標，會使用標準的箭號游標。  
  
 兩個圖示都支援單一文件類型的 MDI 應用程式： 一個主要的應用程式圖示，圖示的文件 MDIChild windows 的其他圖示。 多個文件型別具有不同的圖示，您必須註冊其他`WNDCLASS`es 或使用[CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)函式。  
  
 `CFrameWnd::LoadFrame`將註冊`WNDCLASS`使用您指定做為第一個參數，以及下列的標準屬性的圖示識別碼：  
  
-   類別樣式： CS_DBLCLKS &#124;CS_HREDRAW &#124;CS_VREDRAW;  
  
-   AFX_IDI_STD_FRAME 圖示  
  
-   箭號游標  
  
-   COLOR_WINDOW 背景色彩  
  
 背景色彩和資料指標的值[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)後的工作區不會使用`CMDIFrameWnd`完全覆蓋**MDICLIENT**視窗。 Microsoft 不會鼓勵子類別化**MDICLIENT**視窗，因此使用的資料指標類型，盡可能與標準色彩。  
  
## <a name="subclassing-and-superclassing-controls"></a>子類別化和 Superclassing 控制項  
 如果您子類別化或超級類別 Windows 控制 (例如， [CButton](../mfc/reference/cbutton-class.md)) 則您的類別會自動取得`WNDCLASS`該控制項的 Windows 實作中提供的屬性。  
  
## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 函式  
 MFC 提供 helper 函式，來註冊視窗類別。 提供一組屬性 （視窗類別樣式、 游標、 背景筆刷和圖示），會產生綜合的名稱，並已產生的視窗類別登錄。 例如，套用至物件的  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```  
  
 此函數會傳回暫存產生的已註冊的視窗類別名稱的字串。 如需此函式的詳細資訊，請參閱[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)。  
  
 傳回的字串是靜態字串緩衝區的暫存指標。 是有效的下一個呼叫`AfxRegisterWndClass`。 如果您想要保留此字串周圍，將它存放在[CString](../atl-mfc-shared/using-cstring.md)變數，如此範例所示：  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);

...  
```  
  
 `AfxRegisterWndClass`將會擲回[CResourceException](../mfc/reference/cresourceexception-class.md)如果視窗類別登錄失敗 （因為不正確的參數，或 Windows 記憶體不足）。  
  
## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass 和 AfxRegisterClass 函式  
 如果您想要的任何項目更複雜的什麼`AfxRegisterWndClass`提供，您可以呼叫 Windows API`RegisterClass`或 MFC 函式`AfxRegisterClass`。 `CWnd`， [CFrameWnd](../mfc/reference/cframewnd-class.md)和[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create`函式會接受`lpszClassName`視窗類別的第一個參數的字串名稱。 您可以使用任何已註冊的視窗類別名稱，不論您用來註冊它的方法。  
  
 請務必使用`AfxRegisterClass`(或`AfxRegisterWndClass`) 中的 Win32 DLL。 Win32 不會自動取消註冊 dll，登錄，因此您必須明確地取消登錄類別終止 DLL 的類別。 使用`AfxRegisterClass`而不是`RegisterClass`這可讓您自動處理。 `AfxRegisterClass`會維護一份唯一類別，您的 DLL 註冊，而且將會自動取消登錄 DLL 終止時。 當您使用`RegisterClass`在 DLL 中，您必須確定 DLL 終止時，會取消註冊所有類別 (在您[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)函式)。 這樣可能會導致`RegisterClass`意外失敗，另一個用戶端應用程式嘗試使用您的 DLL。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

