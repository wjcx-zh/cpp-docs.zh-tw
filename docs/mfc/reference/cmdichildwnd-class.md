---
title: CMDIChildWnd 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 995e0ed8dc9d04dd67cd1f4521d4550ccdad36fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390167"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 類別

提供 Windows 多重文件介面 (MDI) 子視窗的功能，以及管理視窗的成員。

## <a name="syntax"></a>語法

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|建構 `CMDIChildWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|建立相關聯的 Windows MDI 子視窗`CMDIChildWnd`物件。|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|傳回父 MDI 用戶端視窗的 MDI 框架。|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|啟動這個 MDI 子視窗。|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|終結此 MDI 子視窗。|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|最大化這個 MDI 子視窗。|
|[CMDIChildWnd::MDIRestore](#mdirestore)|還原這個 MDI 子視窗最大化或最小化的大小。|
|[CMDIChildWnd::SetHandles](#sethandles)|設定功能表和快速鍵資源控制代碼。|

## <a name="remarks"></a>備註

MDI 子視窗看起來很像一般的框架視窗中，不同之處在於 MDI 子視窗會出現在 MDI 框架視窗內，而不是在桌面上。 MDI 子視窗並沒有自己的功能表列，但改為共用，MDI 框架視窗的功能表。 此架構會自動變更 MDI 框架功能表來代表目前現用的 MDI 子視窗。

若要建立有用的 MDI 子視窗應用程式，衍生的類別`CMDIChildWnd`。 將成員變數新增至衍生的類別，以儲存您的應用程式特定的資料。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

有三種方式可建構的 MDI 子視窗：

- 直接建構使用`Create`。

- 直接建構使用`LoadFrame`。

- 間接透過文件範本來建構它。

在呼叫之前`Create`或是`LoadFrame`，您必須建構使用 c + + 堆積上的框架視窗物件**新**運算子。 然後再呼叫`Create`您也可以註冊視窗類別[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式，可將框架的圖示和類別樣式。

使用`Create`傳遞畫面格的建立參數為立即的引數的成員函式。

`LoadFrame` 需要較少的引數比`Create`，並改為擷取資源，包括畫面格的標題、 圖示、 快速鍵對應表，以及功能表中的大部分的預設值。 若要可供`LoadFrame`，所有這些資源必須有相同的資源識別碼 (例如，IDR_MAINFRAME)。

當`CMDIChildWnd`物件包含檢視表和文件，它們藉由間接的架構，而不是直接由程式設計師。 `CDocTemplate`物件用來協調建立框架的、 包含檢視中，建立和檢視，以適當的文件的連接。 參數`CDocTemplate`建構函式指定`CRuntimeClass`三個類別的相關 （文件、 框架和檢視）。 A `CRuntimeClass` framework 會使用物件以動態方式建立新的畫面格時由使用者 （例如，藉由使用新檔案的命令或 MDI 視窗中新的命令）。

框架視窗類別衍生自`CMDIChildWnd`必須宣告與 DECLARE_DYNCREATE，為了讓上述 RUNTIME_CLASS 機制才能正常運作。

`CMDIChildWnd`類別會繼承來自其預設實作的許多`CFrameWnd`。 如需這些功能的詳細清單，請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別描述。 `CMDIChildWnd`類別具有下列額外的功能：

- 搭配`CMultiDocTemplate`類別，多個`CMDIChildWnd`從相同的文件範本的物件會共用相同的功能表中，儲存 Windows 系統資源。

- 目前現用 MDI 子視窗的功能表完全取代 MDI 框架視窗的功能表和目前現用的 MDI 子視窗的標題會加入至 MDI 框架視窗的標題。 進一步實作搭配 MDI 框架視窗的 MDI 子視窗函數的範例，請參閱`CMDIFrameWnd`類別描述。

不使用 c + +**刪除**終結框架視窗的運算子。 請改用 `CWnd::DestroyWindow`。 `CFrameWnd`實作`PostNcDestroy`終結視窗時，將會刪除 c + + 物件。 當使用者關閉框架視窗時，預設值`OnClose`處理常式會呼叫`DestroyWindow`。

如需詳細資訊`CMDIChildWnd`，請參閱 <<c2> [ 框架 Windows](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

呼叫來建構`CMDIChildWnd`物件。

```
CMDIChildWnd();
```

### <a name="remarks"></a>備註

呼叫`Create`建立可見的視窗。

### <a name="example"></a>範例

  範例，請參閱[CMDIChildWnd::Create](#create)。

##  <a name="create"></a>  CMDIChildWnd::Create

呼叫此成員函式，來建立 Windows MDI 子視窗，並將其附加至`CMDIChildWnd`物件。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*lpszClassName*<br/>
指向以 null 結尾的字元字串，可命名 Windows 類別 ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)結構)。 類別名稱可以是任何名稱向[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式。 應該是 NULL，來為標準`CMDIChildWnd`。

*lpszWindowName*<br/>
指向以 null 結束的字元字串，表示視窗名稱。 用來作為文字的標題列。

*cheaderctrl:: Create*<br/>
指定時間範圍[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。 WS_CHILD 樣式是必要的。

*rect*<br/>
包含大小和視窗的位置。 `rectDefault`值表示允許指定的大小和位置的新 Windows `CMDIChildWnd`。

*pParentWnd*<br/>
指定視窗的父代。 如果是 NULL，則會使用主應用程式視窗。

*pContext*<br/>
指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

目前現用的 MDI 子框架視窗可以判斷父框架視窗的標題。 這項功能會停用子框架視窗的 FWS_ADDTOTITLE 樣式位元為關閉。

架構會呼叫此成員函式以回應使用者命令來建立子視窗，以及架構會使用*pContext*正確地連線到應用程式的 子視窗的參數。 當您呼叫`Create`， *pContext*可以是 NULL。

### <a name="example"></a>範例

範例 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>範例

範例 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

呼叫此函式可傳回 MDI 父框架。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>傳回值

MDI 父框架視窗指標。

### <a name="remarks"></a>備註

傳回的框架會移除兩個父代`CMDIChildWnd`，為的型別，可管理 MDICLIENT 視窗的父系`CMDIChildWnd`物件。 呼叫[GetParent](../../mfc/reference/cwnd-class.md#getparent)成員函式來傳回`CMDIChildWnd`做為暫存物件的直屬 MDICLIENT 父`CWnd`指標。

### <a name="example"></a>範例

  範例，請參閱[CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)。

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

呼叫此成員函式可啟用與 MDI 框架視窗無關的 MDI 子視窗。

```
void MDIActivate();
```

### <a name="remarks"></a>備註

當框架變成作用中時，將一併啟用上次啟動的子視窗。

### <a name="example"></a>範例

  範例，請參閱[CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)。

##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy

呼叫此成員函式，要終結之 MDI 子視窗。

```
void MDIDestroy();
```

### <a name="remarks"></a>備註

此成員函式從框架視窗中移除子視窗的標題，並停用子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize

呼叫此成員函式，以最大化的 MDI 子視窗。

```
void MDIMaximize();
```

### <a name="remarks"></a>備註

子視窗會最大化時，Windows 會調整大小，使其填滿的框架視窗工作區的工作區。 Windows 會放置在框架的功能表列中子視窗的 [控制] 功能表，讓使用者可以還原或關閉子視窗，並將子視窗的標題加入至框架視窗標題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore

呼叫此成員函式，若要最大化或最小化的大小從還原的 MDI 子視窗。

```
void MDIRestore();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles

設定功能表和快速鍵資源控制代碼。

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
功能表資源的控制代碼。

*hAccel*<br/>
加速器資源的控制代碼。

### <a name="remarks"></a>備註

呼叫此函式可設定使用 MDI 子視窗物件的功能表和快速鍵資源。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../visual-cpp-samples.md)<br/>
[MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)
