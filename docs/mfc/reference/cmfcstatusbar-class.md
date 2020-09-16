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
ms.openlocfilehash: 004873ef2696eb9504cdd4df77e700c4a145e886
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686570"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar 類別

`CMFCStatusBar`類別會執行類似于類別的狀態列 `CStatusBar` 。 不過， `CMFCStatusBar` 類別具有 `CStatusBar` 類別所未提供的功能，例如能夠顯示影像、動畫和進度列，而且能夠回應滑鼠按兩下。

如需詳細資訊，請參閱位於 Visual Studio 安裝的 **VC \\ atlmfc \\ src \\ mfc** 資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCStatusBar：： CalcFixedLayout](#calcfixedlayout)| (覆寫 [CBasePane：： CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。 ) |
|[CMFCStatusBar：： CommandToIndex](#commandtoindex)||
|[CMFCStatusBar：： Create](#create)|建立控制列，並將它附加至 [CPane](../../mfc/reference/cpane-class.md) 物件。  (覆寫 [CPane：： Create](../../mfc/reference/cpane-class.md#create). ) |
|[CMFCStatusBar：： CreateEx](#createex)|建立控制列，並將它附加至 [CPane](../../mfc/reference/cpane-class.md) 物件。  (覆寫 [CPane：： CreateEx](../../mfc/reference/cpane-class.md#createex)。 ) |
|[CMFCStatusBar：:D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|決定是否可以在這個窗格和父框架之間動態插入另一個窗格。  (覆寫 [CBasePane：:D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。 ) |
|[CMFCStatusBar：： EnablePaneDoubleClick](#enablepanedoubleclick)|啟用或停用在狀態列上按兩下滑鼠的處理。|
|[CMFCStatusBar：： EnablePaneProgressBar](#enablepaneprogressbar)|在指定的窗格上顯示進度列。|
|[CMFCStatusBar：： GetCount](#getcount)|傳回狀態列上的窗格數目。|
|[CMFCStatusBar：： GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar：： GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar：： GetItemID](#getitemid)||
|[CMFCStatusBar：： GetItemRect](#getitemrect)||
|[CMFCStatusBar：： GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar：： GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar：： GetPaneStyle](#getpanestyle)|傳回窗格樣式。  (覆寫 [CBasePane：： GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle)。 ) |
|[CMFCStatusBar：： GetPaneText](#getpanetext)||
|[CMFCStatusBar：： GetPaneWidth](#getpanewidth)|傳回狀態列的指定窗格寬度（以圖元為單位）。|
|[CMFCStatusBar：： GetTipText](#gettiptext)|傳回狀態列之指定窗格的工具提示文字。|
|[CMFCStatusBar：： InvalidatePaneContent](#invalidatepanecontent)|使指定的窗格失效並重新繪製其內容。|
|[CMFCStatusBar：:P reCreateWindow](#precreatewindow)|在建立附加至此物件的 Windows 視窗之前，由架構呼叫 `CWnd` 。  (覆寫 [CWnd：:P recreatewindow](../../mfc/reference/cwnd-class.md#precreatewindow)。 ) |
|[CMFCStatusBar：： SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar：： SetIndicators](#setindicators)||
|[CMFCStatusBar：： SetPaneAnimation](#setpaneanimation)|將動畫指派給指定的窗格。|
|[CMFCStatusBar：： SetPaneBackgroundColor](#setpanebackgroundcolor)|設定狀態列之指定窗格的背景色彩。|
|[CMFCStatusBar：： SetPaneIcon](#setpaneicon)|設定狀態列的指定窗格的指標圖示。|
|[CMFCStatusBar：： SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar：： SetPaneProgress](#setpaneprogress)|針對狀態列的指定窗格，設定進度列的目前進度。|
|[CMFCStatusBar：： SetPaneStyle](#setpanestyle)|設定窗格的樣式。  (覆寫 [CBasePane：： SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。 ) |
|[CMFCStatusBar：： SetPaneText](#setpanetext)||
|[CMFCStatusBar：： SetPaneTextColor](#setpanetextcolor)|設定狀態列之指定窗格的文字色彩。|
|[CMFCStatusBar：： SetPaneWidth](#setpanewidth)|設定狀態列的指定窗格寬度（以圖元為單位）。|
|[CMFCStatusBar：： SetTipText](#settiptext)|設定狀態列之指定窗格的工具提示文字。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCStatusBar：： OnDrawPane](#ondrawpane)|在重新繪製狀態列的窗格時由架構呼叫。|

## <a name="remarks"></a>備註

下圖顯示狀態列的狀態列 [示範範例](../../overview/visual-cpp-samples.md) 應用程式的圖表。

![CMFCStatusBar 範例](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar 範例")

## <a name="examples"></a>範例

下列範例會示範應用程式用來在類別中呼叫各種方法的本機變數 `CMFCStatusBar` 。 這些變數是在 StatusBarDemoView 中宣告。 主要框架是在 Mainfrm.cpp 中宣告，檔是在 StatusBarDemoDoc 中宣告，而視圖則是在 StatusBarDemoView 中宣告。 此程式碼片段是 [狀態列示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

下列範例示範如何在 `CMFCStatusBar` mainfrm.cpp 中引進 `GetStatusBar` 方法，然後從 StatusBarDemoView 中的方法呼叫這個方法，以取得物件的參考 `GetStatusBar` 。 此程式碼片段是 [狀態列示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

下列範例示範如何在 StatusBarDemoView 中呼叫類別中的各種方法。 `CMFCStatusBar` 常數是在 Mainfrm.cpp 中宣告。 此範例示範如何設定圖示、設定狀態列窗格的工具提示文字、在指定的窗格上顯示進度列、指派動畫到指定的窗格、設定狀態列窗格的文字和寬度，以及為狀態列窗格設定進度列的目前進度指標。 此程式碼片段是 [狀態列示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxstatusbar。h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCStatusBar：： CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

在 *bStretch*<br/>
在 *bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a> CMFCStatusBar：： CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

在 *nIDFind*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarcreate"></a><a name="create"></a> CMFCStatusBar：： Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

在 *pParentWnd*<br/>
在 *dwStyle*<br/>
在 *nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a> CMFCStatusBar：： CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

在 *pParentWnd*<br/>
在 *dwCtrlStyle*<br/>
在 *dwStyle*<br/>
在 *nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCStatusBar：:D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a> CMFCStatusBar：： EnablePaneDoubleClick

啟用或停用在狀態列上按兩下滑鼠的處理。

```cpp
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在若為 TRUE，則啟用滑鼠按兩下的處理。 否則，請停用滑鼠按兩下的處理。

### <a name="remarks"></a>備註

如果已啟用狀態列來處理按兩下，Windows 會在每次使用者按兩下狀態列窗格時，將 WM_COMMAND 通知連同資源識別碼傳送給狀態列的擁有者。

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a> CMFCStatusBar：： EnablePaneProgressBar

在指定的窗格上顯示進度列。

```cpp
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
在指定要啟用其進度列之窗格的索引。

*nTotal*<br/>
在指定進度列的最大值。

*bDisplayText*<br/>
在指定進度列是否應顯示目前的進度值。

*clrBar*<br/>
在指定進度列的背景色彩。

*clrBarDest*<br/>
在指定進度列背景的次要色彩。 使用與 *clrBar* 不同的值，以將混合成漸層的色彩填滿。

*clrProgressText*<br/>
在指定進度列的文字色彩。

### <a name="remarks"></a>備註

如果您想要停用 NTotal 的進度列呼叫，請 `EnablePaneProgressBar` 將其設定為-1。 *nTotal* 依預設， *nTotal* 會設定為100。 因此，您不需要任何額外的計算，就能以百分比顯示進度。

您應針對 *clrBar* 和 *clrBarDest* 傳遞不同的值，以便進度列的背景色彩會顯示混合成漸層的色彩。 .

若要設定目前的進度，請呼叫 [CMFCStatusBar：： SetPaneProgress](#setpaneprogress) 方法。

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a> CMFCStatusBar：： GetCount

抓取狀態列中的窗格數目。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

狀態列中的窗格數目。

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a> CMFCStatusBar：： GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a> CMFCStatusBar：： GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>參數

在 *rect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a> CMFCStatusBar：： GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a> CMFCStatusBar：： GetItemRect

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>
在 *lpRect*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> CMFCStatusBar：： GetPaneInfo

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>
在 *nID*<br/>
在 *nStyle*<br/>
在 *cxWidth*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a> CMFCStatusBar：： GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a> CMFCStatusBar：： GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a> CMFCStatusBar：： GetPaneText

```cpp
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>
在 *s*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a> CMFCStatusBar：： GetPaneWidth

抓取狀態列的窗格寬度。

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定狀態列窗格的索引。

### <a name="return-value"></a>傳回值

*NIndex*指定之狀態列窗格的寬度;否則，如果狀態列窗格不存在，則為零。

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a> CMFCStatusBar：： GetTipText

取得狀態列窗格的工具提示文字。

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定要取得其工具提示文字之窗格的索引。

### <a name="return-value"></a>傳回值

*NIndex*指定之狀態列窗格的工具提示文字。 否則，如果指定的 *nIndex* 不存在狀態列窗格，或其工具提示文字是空的，則為空字串。

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a> CMFCStatusBar：： InvalidatePaneContent

使狀態列窗格失效並重新繪製其內容。

```cpp
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定要失效並重新繪製其內容的窗格索引。

### <a name="remarks"></a>備註

當狀態列失效時，就會標示為重新繪製。 當 `UpdateWindow` 方法將 WM_PAINT 訊息傳送給方法時，Windows 會重新繪製它 `OnPaint` 。

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a> CMFCStatusBar：： OnDrawPane

重新繪製狀態列的窗格。

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在要繪製之裝置內容的指標。

*pPane*<br/>
在 `CMFCStatusBarPaneInfo` 結構的指標，其中包含要重繪之窗格的相關資訊。

### <a name="remarks"></a>備註

根據預設，會 `OnDrawPane` 根據窗格的樣式和內容，使用裝置內容 *pDC* 來重繪窗格。

在衍生的類別中覆寫這個方法 `CMFCStatusBar` ，以自訂窗格的外觀。

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a> CMFCStatusBar：:P reCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>參數

在 *cs*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a> CMFCStatusBar：： SetDrawExtendedArea

```cpp
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

在 *bSet*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a> CMFCStatusBar：： SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

在 *lpIDArray*<br/>
在 *nIDCount*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a> CMFCStatusBar：： SetPaneAnimation

將動畫指派給指定的窗格。

```cpp
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定您想要為其指派動畫之窗格的索引。

*hImageList*<br/>
在指定包含動畫框架的影像清單控制碼。

*nFrameRate*<br/>
在指定動畫的畫面播放速率（以毫秒為單位）。

*bUpdate*<br/>
在若為 TRUE，請立即更新窗格內容。 否則，當窗格內容失效時，就會更新該內容。

### <a name="remarks"></a>備註

如果您想要停用目前的動畫，請呼叫 `SetPaneAnimation` 並 `hImageList` 將設定為 Null。

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a> CMFCStatusBar：： SetPaneBackgroundColor

設定狀態列窗格的背景色彩。

```cpp
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定要設定新背景色彩之窗格的索引。

*clrBackground*<br/>
在指定新的背景色彩。

*bUpdate*<br/>
在若為 TRUE，請立即更新窗格內容。 否則，請不要更新窗格內容，直到窗格被另一個方法失效為止。

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a> CMFCStatusBar：： SetPaneIcon

設定狀態列窗格的圖示。

```cpp
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
在指定要設定影像之窗格的索引。

*hIcon*<br/>
在指定要設定為窗格影像的圖示控制碼。

*bUpdate*<br/>
在指定是否立即更新窗格內容。

*hBmp*<br/>
在指定要設定為窗格影像之點陣圖的控制碼。

*clrTransparent*<br/>
在指定 *hBmp* 所指出點陣圖的透明色彩。

### <a name="remarks"></a>備註

您可以將 HICON 或 HBITMAP 與透明色彩一起傳遞，以設定窗格的影像。 如果您不想再顯示影像，請傳遞 Null 值作為影像控制碼。

如果有任何正在執行的動畫 [CMFCStatusBar：： SetPaneAnimation](#setpaneanimation) 已設定，則動畫將會停止。

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> CMFCStatusBar：： SetPaneInfo

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>
在 *nID*<br/>
在 *nStyle*<br/>
在 *cxWidth*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a> CMFCStatusBar：： SetPaneProgress

針對指定的窗格，設定進度列的目前進度指標。

```cpp
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定要更新進度指標之窗格的索引。

*nCurr*<br/>
在指定進度指標的目前值。

*bUpdate*<br/>
在指定是否應該立即更新窗格。

### <a name="remarks"></a>備註

當您想要在指定的窗格中更新進度列的進度指示器時，請呼叫這個方法。

若要在指定的窗格中使用此函數，您必須先呼叫 [CMFCStatusBar：： EnablePaneProgressBar](#enablepaneprogressbar) 。

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a> CMFCStatusBar：： SetPaneStyle

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>
在 *nStyle*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a> CMFCStatusBar：： SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>參數

在 *nIndex*<br/>
在 *lpszNewText*<br/>
在 *bUpdate*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a> CMFCStatusBar：： SetPaneTextColor

設定指定之窗格的文字色彩。

```cpp
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在指定要指派新文字色彩之窗格的索引。

*clrText*<br/>
在指定文字色彩。

*bUpdate*<br/>
在若為 TRUE，請立即更新窗格內容。 否則，請不要更新窗格內容，直到窗格被另一個方法失效為止。

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a> CMFCStatusBar：： SetPaneWidth

設定狀態列窗格的寬度。

```cpp
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在要設定新寬度的狀態列窗格索引。

*殘雪*<br/>
在狀態列窗格的新寬度（以圖元為單位）。

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a> CMFCStatusBar：： SetTipText

設定狀態列窗格的工具提示文字。

```cpp
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在您要指派工具提示文字之窗格的索引。

*pszTipText*<br/>
在新的工具提示文字。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPane 類別](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)
