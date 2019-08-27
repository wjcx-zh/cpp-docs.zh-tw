---
title: CMDIChildWnd 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 09a9846cc3d242ef7d812cb31b4dcdd515d5f6ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506084"
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
|[CMDIChildWnd:: CMDIChildWnd](#cmdichildwnd)|建構 `CMDIChildWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|建立與`CMDIChildWnd`物件相關聯的 Windows MDI 子視窗。|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|傳回 MDI 用戶端視窗的父 MDI 框架。|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|啟用此 MDI 子視窗。|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|終結此 MDI 子視窗。|
|[CMDIChildWnd:: MDIMaximize](#mdimaximize)|將此 MDI 子視窗最大化。|
|[CMDIChildWnd:: MDIRestore](#mdirestore)|從最大化或最小化的大小還原此 MDI 子視窗。|
|[CMDIChildWnd::SetHandles](#sethandles)|設定功能表和快速鍵資源的控制碼。|

## <a name="remarks"></a>備註

MDI 子視窗看起來很像一般框架視窗, 不同之處在于 MDI 子視窗會出現在 MDI 框架視窗內部, 而不是在桌面上。 MDI 子視窗沒有自己的功能表列, 而是會共用 MDI 框架視窗的功能表。 架構會自動變更 MDI 框架功能表, 以代表目前現用的 MDI 子視窗。

若要為您的應用程式建立有用的 MDI 子視窗, 請`CMDIChildWnd`從衍生類別。 將成員變數加入至衍生類別, 以儲存應用程式特定的資料。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

有三種方式可建立 MDI 子視窗:

- 使用`Create`直接進行結構。

- 使用`LoadFrame`直接進行結構。

- 透過檔範本間接加以建立。

在您呼叫`Create`或`LoadFrame`之前, 您必須使用C++ **new**運算子, 在堆積上建立框架視窗物件。 在呼叫`Create`之前, 您也可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式來註冊視窗類別, 以設定框架的圖示和類別樣式。

`Create`使用成員函式, 將框架的建立參數當做直接引數傳遞。

`LoadFrame`需要的引數`Create`數目少於, 而是從資源中抓取大部分的預設值, 包括框架的標題、圖示、快速鍵對應表和功能表。 若要讓能夠`LoadFrame`存取, 所有這些資源都必須具有相同的資源識別碼 (例如, IDR_MAINFRAME)。

`CMDIChildWnd`當物件包含視圖和檔時, 架構會間接建立它們, 而不是直接由程式設計人員建立。 `CDocTemplate`物件會協調框架的建立、建立包含的視圖, 以及將視圖連接到適當的檔。 此函式的`CDocTemplate`參數會`CRuntimeClass`指定涉及的三個類別 (檔、框架和視圖) 的。 當使用者指定時, 架構會使用物件以動態方式建立新的框架(例如,藉由使用[檔案][新增]命令或[MDI視窗][新增]命令)。`CRuntimeClass`

衍生自`CMDIChildWnd`的框架視窗類別必須以 DECLARE_DYNCREATE 宣告, 上述 RUNTIME_CLASS 機制才能正常運作。

類別`CMDIChildWnd`會從`CFrameWnd`繼承其大部分的預設實作為。 如需這些功能的詳細清單, 請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別描述。 `CMDIChildWnd`類別具有下列其他功能:

- 與`CMultiDocTemplate`類別搭配使用時, 相同`CMDIChildWnd`檔範本中的多個物件會共用相同的功能表, 並儲存 Windows 系統資源。

- 目前作用中的 MDI 子視窗功能表會完全取代 MDI 框架視窗的功能表, 而目前作用中 MDI 子視窗的標題會加入至 MDI 框架視窗的標題。 如需與 mdi 框架視窗一起執行之 mdi 子視窗函數的進一步範例, 請參閱`CMDIFrameWnd`類別描述。

請勿使用C++ **delete**運算子來摧毀框架視窗。 請改用 `CWnd::DestroyWindow`。 當`CFrameWnd`視窗終結`PostNcDestroy`時, 的C++執行將會刪除物件。 當使用者關閉框架視窗時, 預設`OnClose`處理常式將會呼叫。 `DestroyWindow`

如需的詳細`CMDIChildWnd`資訊, 請參閱[框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cmdichildwnd"></a>CMDIChildWnd:: CMDIChildWnd

呼叫以建立`CMDIChildWnd`物件。

```
CMDIChildWnd();
```

### <a name="remarks"></a>備註

呼叫`Create`以建立可見視窗。

### <a name="example"></a>範例

  請參閱[CMDIChildWnd:: Create](#create)的範例。

##  <a name="create"></a>CMDIChildWnd:: Create

呼叫這個成員函式以建立 Windows MDI 子視窗, 並將它附加`CMDIChildWnd`至物件。

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
指向以 null 結束的字元字串, 其命名為 Windows 類別 ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構)。 類別名稱可以是任何向[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函數註冊的名稱。 標準`CMDIChildWnd`的應該是 Null。

*lpszWindowName*<br/>
指向表示視窗名稱的以 null 結束的字元字串。 當做標題列的文字使用。

*dwStyle*<br/>
指定視窗[樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。 需要 WS_CHILD 樣式。

*rect*<br/>
包含視窗的大小和位置。 此`rectDefault`值可讓 Windows 指定新`CMDIChildWnd`的大小和位置。

*pParentWnd*<br/>
指定視窗的父系。 如果是 Null, 則會使用主應用程式視窗。

*pContext*<br/>
指定[CCreateCoNtext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是 Null。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

目前現用的 MDI 子框架視窗可以決定父框架視窗的標題。 關閉子框架視窗的 FWS_ADDTOTITLE 樣式位, 即可停用這項功能。

架構會呼叫這個成員函式, 以回應使用者命令以建立子視窗, 而架構會使用*pCoNtext*參數, 將子視窗正確地連接到應用程式。 當您呼叫`Create`時, *pCoNtext*可以是 Null。

### <a name="example"></a>範例

範例 1：

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>範例

範例 2：

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>CMDIChildWnd:: GetMDIFrame

呼叫此函式可傳回 MDI 父框架。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>傳回值

MDI 父框架視窗的指標。

### <a name="remarks"></a>備註

傳回的畫面格是從移除的`CMDIChildWnd`兩個父代, 而且是`CMDIChildWnd`管理物件之 MDICLIENT 類型視窗的父系。 呼叫[GetParent](../../mfc/reference/cwnd-class.md#getparent)成員函式, 將`CMDIChildWnd`物件的立即 MDICLIENT 父系當做暫存`CWnd`指標傳回。

### <a name="example"></a>範例

  請參閱[CMDIFrameWnd:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)的範例。

##  <a name="mdiactivate"></a>CMDIChildWnd:: MDIActivate

呼叫這個成員函式可獨立于 MDI 框架視窗之外, 啟用 MDI 子視窗。

```
void MDIActivate();
```

### <a name="remarks"></a>備註

當畫面格變成作用中狀態時, 最後啟動的子視窗也會一併啟用。

### <a name="example"></a>範例

  請參閱[CMDIFrameWnd:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)的範例。

##  <a name="mdidestroy"></a>CMDIChildWnd:: MDIDestroy

呼叫這個成員函式以終結 MDI 子視窗。

```
void MDIDestroy();
```

### <a name="remarks"></a>備註

成員函式會從框架視窗中移除子視窗的標題, 並停用子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>CMDIChildWnd:: MDIMaximize

呼叫這個成員函式可將 MDI 子視窗最大化。

```
void MDIMaximize();
```

### <a name="remarks"></a>備註

當子視窗最大化時, Windows 會將其調整大小, 使其工作區填滿框架視窗的工作區。 Windows 會將子視窗的 [控制] 功能表放在框架的功能表列中, 讓使用者可以還原或關閉子視窗, 並將子視窗的標題加入框架視窗標題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>CMDIChildWnd:: MDIRestore

呼叫這個成員函式可從最大化或最小化的大小還原 MDI 子視窗。

```
void MDIRestore();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>CMDIChildWnd:: SetHandles

設定功能表和快速鍵資源的控制碼。

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
功能表資源的控制碼。

*hAccel*<br/>
快速鍵資源的控制碼。

### <a name="remarks"></a>備註

呼叫此函式可設定 MDI 子視窗物件所使用的功能表和快速鍵資源。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)
