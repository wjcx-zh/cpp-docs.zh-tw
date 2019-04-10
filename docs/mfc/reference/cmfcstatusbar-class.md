---
title: CMFCStatusBar 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 87f75769e2f400a7721a8c9089d6c5596c31a4e3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775955"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar 類別

`CMFCStatusBar`類別會實作類似於狀態列`CStatusBar`類別。 不過， `CMFCStatusBar` 類別具有 `CStatusBar` 類別所未提供的功能，例如能夠顯示影像、動畫和進度列，而且能夠回應滑鼠按兩下。

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

## <a name="syntax"></a>語法

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(覆寫[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Create](#create)|會建立一種控制列，並將它附加至[CPane](../../mfc/reference/cpane-class.md)物件。 (覆寫[cpane:: Create](../../mfc/reference/cpane-class.md#create)。)|
|[CMFCStatusBar::CreateEx](#createex)|會建立一種控制列，並將它附加至[CPane](../../mfc/reference/cpane-class.md)物件。 (覆寫[cpane:: Createex](../../mfc/reference/cpane-class.md#createex)。)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|判斷是否可以此窗格與父框架之間動態插入另一個窗格。 (覆寫[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|啟用或停用則會在狀態列上按兩下滑鼠的處理。|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|顯示進度列上指定的窗格。|
|[CMFCStatusBar::GetCount](#getcount)|在 [狀態] 列上傳回窗格的數目。|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|傳回的窗格樣式。 (覆寫[CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle)。)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|傳回寬度，單位為像素指定狀態列的窗格。|
|[CMFCStatusBar::GetTipText](#gettiptext)|傳回指定的窗格的 [狀態] 列的工具提示文字。|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|失效的指定的窗格，並重新繪製其內容。|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|由架構建立附加至此 Windows 視窗前呼叫`CWnd`物件。 (覆寫[CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|將動畫指派給指定的窗格中。|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|設定指定的窗格的 [狀態] 列的背景色彩。|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|設定指定的窗格的 [狀態] 列的指標圖示。|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|設定指定的狀態列窗格的進度列目前的進度。|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|設定窗格的樣式。 (覆寫[CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|設定指定的窗格的 [狀態] 列的文字色彩。|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|設定像素為單位的指定窗格的 [狀態] 列的寬度。|
|[CMFCStatusBar::SetTipText](#settiptext)|設定指定的窗格的 [狀態] 列的工具提示文字。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|它會重新繪製的狀態列窗格時，由架構呼叫。|

## <a name="remarks"></a>備註

下圖顯示從 [狀態] 列的圖形[狀態列示範範例](../../overview/visual-cpp-samples.md)應用程式。

![Cmfcstatusbar 範例](../../mfc/reference/media/cmfcstatusbar.png "cmfcstatusbar 範例")

## <a name="example"></a>範例

下列範例示範應用程式使用各種方法呼叫中的本機變數`CMFCStatusBar`類別。 StatusBarDemoView.h 中宣告這些變數。 主框架中稱為 MainFrm.h 宣告、 文件宣告中 StatusBarDemoDoc.h，因此 StatusBarDemoView.h 中宣告檢視。 此程式碼片段是一部分[狀態列示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>範例

下列範例示範如何取得的參考`CMFCStatusBar`物件，藉由引進`GetStatusBar`中稱為 MainFrm.h 和呼叫這個方法，從方法`GetStatusBar`StatusBarDemoView.h 中的方法。 此程式碼片段是一部分[狀態列示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>範例

下列範例示範如何呼叫各種方法`CMFCStatusBar`StatusBarDemoView.cpp 中的類別。 常數宣告中稱為 MainFrm.h。 此範例示範如何設定圖示、 設定狀態列窗格的工具提示文字、 顯示進度列上指定的窗格，將指定的窗格中的動畫、 設定文字和寬度的狀態列窗格，以及設定程式的目前進度指示器狀態列窗格的 ess 列。 此程式碼片段是一部分[狀態列示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxstatusbar.h

##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

[in] *nIDFind*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="create"></a>  CMFCStatusBar::Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

[in] *pParentWnd*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="createex"></a>  CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

[in] *pParentWnd*<br/>
[in] *dwCtrlStyle*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick

啟用或停用則會在狀態列上按兩下滑鼠的處理。

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]如果為 TRUE，可讓滑鼠按兩下滑鼠左鍵的處理。 否則，請停用滑鼠按兩下滑鼠左鍵的處理。

### <a name="remarks"></a>備註

如果處理 double 點選啟用 [狀態] 列，則 Windows 會傳送 WM_COMMAND 通知資源識別碼以及每次使用者按兩下狀態列窗格上狀態列的擁有者。

##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar

顯示進度列上指定的窗格。

```
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]若要啟用其進度列指定窗格的索引。

*nTotal*<br/>
[in]指定進度列的最大值。

*bDisplayText*<br/>
[in]指定是否要在進度列顯示目前的進度值。

*clrBar*<br/>
[in]指定進度列的背景色彩。

*clrBarDest*<br/>
[in]指定進度列背景的次要色彩。 使用不同的值*clrBar*以混合成漸層的色彩填滿。

*clrProgressText*<br/>
[in]指定進度列的文字色彩。

### <a name="remarks"></a>備註

如果您想要停用進度列呼叫`EnablePaneProgressBar`具有*nTotal*設為-1。 依預設*nTotal*設為 100。 因此，您不需要任何額外的計算，以百分比顯示進度。

您應該將不同的值傳給*clrBar*並*clrBarDest* ，讓進度列的背景色彩顯示混合成漸層色彩。 。

若要設定目前的進度，請呼叫[CMFCStatusBar::SetPaneProgress](#setpaneprogress)方法。

##  <a name="getcount"></a>  CMFCStatusBar::GetCount

擷取狀態 列中的窗格數目。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

在 [狀態] 列中的窗格數目。

##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>參數

[in] *rect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>
[in] *lpRect*<br/>

### <a name="remarks"></a>備註

##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>備註

##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>
[in] *s*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth

擷取的狀態列窗格的寬度。

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定狀態列窗格的索引。

### <a name="return-value"></a>傳回值

狀態列窗格的寬度， *nIndex*指定，否則為零如果狀態列窗格不存在。

##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText

擷取的狀態列窗格的工具提示文字。

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定要擷取的工具提示文字窗格的索引。

### <a name="return-value"></a>傳回值

狀態列窗格的工具提示文字所*nIndex*指定。 如果狀態列窗格沒有指定，空的字串，否則為*nIndex*或如果是空的工具提示文字。

##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent

狀態列窗格使其失效並重新繪製其內容。

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定 [內容屬於失效並重新繪製] 窗格的索引。

### <a name="remarks"></a>備註

當 [狀態] 列會失效時，則會將其標示為重新繪製。 Windows 重新繪製時`UpdateWindow`方法會傳送 WM_PAINT 訊息給`OnPaint`方法。

##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane

重繪狀態列的窗格。

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]要繪製的裝置內容指標。

*pPane*<br/>
[in]指標`CMFCStatusBarPaneInfo`結構，其中包含的資訊窗格中重新繪製。

### <a name="remarks"></a>備註

根據預設，`OnDrawPane`所使用的裝置內容，窗格會重繪*pDC*根據窗格的樣式和內容。

覆寫這個方法在`CMFCStatusBar`-衍生的類別，自訂窗格的外觀。

##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>參數

[in] *cs*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

[in] *bSet*<br/>

### <a name="remarks"></a>備註

##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

[in] *lpIDArray*<br/>
[in] *nIDCount*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation

將動畫指派給指定的窗格中。

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定您要指派給它的動畫] 窗格的索引。

*hImageList*<br/>
[in]指定保留動畫畫面格的影像清單的控制代碼。

*nFrameRate*<br/>
[in]指定以毫秒為單位，動畫的畫面播放速率。

*bUpdate*<br/>
[in]如果為 TRUE，請立即更新] 窗格的內容。 否則，它失效時，會更新窗格內容。

### <a name="remarks"></a>備註

如果您想要停用目前的動畫，呼叫`SetPaneAnimation`與`hImageList`設為 NULL。

##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor

設定狀態列窗格的背景色彩。

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定要設定新的背景色彩] 窗格的索引。

*clrBackground*<br/>
[in]指定新的背景色彩。

*bUpdate*<br/>
[in]如果為 TRUE，請立即更新] 窗格的內容。 否則，不會更新窗格內容直到窗格都無效的另一種方法。

##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon

設定狀態列窗格的圖示。

```
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定要設定的映像] 窗格的索引。

*hIcon*<br/>
[in]指定要設定成窗格映像的圖示的控制代碼。

*bUpdate*<br/>
[in]指定是否要立即更新] 窗格的內容。

*hBmp*<br/>
[in]指定要設定窗格映像為點陣圖的控制代碼。

*clrTransparent*<br/>
[in]指定點陣圖的透明色彩的*hBmp*表示。

### <a name="remarks"></a>備註

您可以將傳遞 HICON 或 HBITMAP 設定窗格的影像的透明色彩。 如果不想再顯示影像，傳遞 NULL 值做為影像控點。

如果沒有任何執行中的動畫所[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)已設定時，動畫將會停止。

##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>備註

##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress

設定 [指定] 窗格中的進度列目前的進度列指示器。

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定用來更新進度列指示器之窗格的索引。

*nCurr*<br/>
[in]指定進度列指示器的目前值。

*bUpdate*<br/>
[in]指定是否要立即更新] 窗格。

### <a name="remarks"></a>備註

當您想要更新進度列在 [指定] 窗格中的進度列指示器，請呼叫這個方法。

若要使用此函式指定的窗格，您必須呼叫[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)第一次。

##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>
[in] *nStyle*<br/>

### <a name="remarks"></a>備註

##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>參數

[in] *nIndex*<br/>
[in] *lpszNewText*<br/>
[in] *bUpdate*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor

設定 [指定] 窗格中的文字色彩。

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]指定您要指派新的文字色彩窗格的索引。

*clrText*<br/>
[in]指定的文字色彩。

*bUpdate*<br/>
[in]如果為 TRUE，請立即更新] 窗格的內容。 否則，不會更新窗格內容直到窗格都無效的另一種方法。

##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth

設定狀態列窗格的寬度。

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]要設定新的寬度狀態列窗格的索引。

*cx*<br/>
[in][狀態] 列窗格中，像素為單位的新寬度。

##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText

設定工具提示文字的狀態列窗格。

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]您要指派的工具提示文字窗格的索引。

*pszTipText*<br/>
[in]新的工具提示文字。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPane 類別](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)
