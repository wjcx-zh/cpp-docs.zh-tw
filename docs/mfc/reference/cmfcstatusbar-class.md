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
ms.openlocfilehash: 024fbad44af2fb11e967141fc8e7ccc0aad0ccbe
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753474"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar 類別

類`CMFCStatusBar`實現`CStatusBar`與 類類似的狀態欄。 不過， `CMFCStatusBar` 類別具有 `CStatusBar` 類別所未提供的功能，例如能夠顯示影像、動畫和進度列，而且能夠回應滑鼠按兩下。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC狀態列::鈣固定佈局](#calcfixedlayout)|(覆蓋[CBasePane::CalcFixed 佈局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFC狀態列::命令索引](#commandtoindex)||
|[CMFC 狀態列:建立](#create)|創建控制欄並將其附加到[CPane](../../mfc/reference/cpane-class.md)物件。 (覆蓋[CPane:建立](../../mfc/reference/cpane-class.md#create).)|
|[CMFC 狀態列:建立Ex](#createex)|創建控制欄並將其附加到[CPane](../../mfc/reference/cpane-class.md)物件。 (覆蓋[CPane:createEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFC狀態列::D允許在之前插入](#doesallowdyninsertbefore)|確定是否可以在此窗格和父框架之間動態插入另一個窗格。 (覆蓋[CBasePane::DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFC狀態列::啟用窗格按兩下](#enablepanedoubleclick)|啟用或禁用狀態列上滑鼠按兩下的處理。|
|[CMFC狀態列::啟用窗格進度列](#enablepaneprogressbar)|在指定的窗格上顯示進度列。|
|[CMFC狀態列:取得計數](#getcount)|返回狀態列上的窗格數。|
|[CMFC 狀態列:取得 Draw 擴充區域](#getdrawextendedarea)||
|[CMFC狀態列:取得延伸區域](#getextendedarea)||
|[CMFC狀態列:取得項目ID](#getitemid)||
|[CMFC狀態列:取得專案已重新完成](#getitemrect)||
|[CMFC狀態列:獲取PaneInfo](#getpaneinfo)||
|[CMFC狀態列:抓取窗格進度](#getpaneprogress)||
|[CMFC狀態列:抓取窗格樣式](#getpanestyle)|返回窗格樣式。 (覆蓋[CBasePane::取得窗格樣式](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFC狀態列:抓取窗格文字](#getpanetext)||
|[CMFC狀態列:抓取窗格寬度](#getpanewidth)|返回狀態列指定窗格的寬度(以像素為單位)。|
|[CMFC 狀態列:取得提示文字](#gettiptext)|傳回狀態列指定窗格的工具提示文字。|
|[CMFC 狀態列:無效窗格內容](#invalidatepanecontent)|使指定的窗格無效並重繪其內容。|
|[CMFC狀態列::P重新建立視窗](#precreatewindow)|在創建附加到此`CWnd`物件的 Windows 視窗之前,由框架調用。 (涵蓋[CWnd::P重新建立視窗](../../mfc/reference/cwnd-class.md#precreatewindow)。)|
|[CMFC狀態列::設定 Draw 延伸區域](#setdrawextendedarea)||
|[CMFC狀態列:設定指標](#setindicators)||
|[CMFC狀態列:設定窗格動畫](#setpaneanimation)|將動畫分配給指定的窗格。|
|[CMFC狀態列:設置Pane背景顏色](#setpanebackgroundcolor)|設定狀態列指定窗格的背景顏色。|
|[CMFC 狀態列:設定窗格圖示](#setpaneicon)|設定狀態列指定窗格的指示器圖示。|
|[CMFC狀態列:設定窗格資訊](#setpaneinfo)||
|[CMFC狀態列::設定窗格進度](#setpaneprogress)|設置狀態列指定窗格的進度列的當前進度。|
|[CMFC狀態列:設定窗格樣式](#setpanestyle)|設置窗格的樣式。 (覆蓋[CBasePane::設定窗格樣式](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFC 狀態列:設定窗格文字](#setpanetext)||
|[CMFC 狀態列:設定窗格文字顏色](#setpanetextcolor)|設定狀態列指定窗格的文字顏色。|
|[CMFC狀態列:設定窗格寬度](#setpanewidth)|設置狀態列指定窗格的寬度(以像素為單位)。|
|[CMFC 狀態列:設定提示文字](#settiptext)|為狀態列的指定窗格設置工具提示文本。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC狀態列:在DrawPane上](#ondrawpane)|當框架重繪狀態列的窗格時,由它調用。|

## <a name="remarks"></a>備註

下圖顯示了[狀態列演示範例](../../overview/visual-cpp-samples.md)應用程式中的狀態列的圖形。

![CMFCStatusBar 範例](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar 範例")

## <a name="example"></a>範例

下面的範例演示了應用程式用於調用類中各種方法的`CMFCStatusBar`局部變數。 這些變數在 StatusBarDemoView.h 中聲明。 主框架在 MainFrm.h 中聲明,文檔在 StatusBarDemoDoc.h 中聲明,檢視在 StatusBarDemoView.h 中聲明。 此代碼段是[狀態列演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>範例

下面的示例演示如何通過在 MainFrm.h`CMFCStatusBar``GetStatusBar`中引入 方法,然後從 StatusBarDemoView.h`GetStatusBar`中的方法調用此方法來獲取對物件的引用。 此代碼段是[狀態列演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>範例

下面的範例展示如何在 StatusBarDemoView.cpp`CMFCStatusBar`中的類中呼叫各種方法。 常量在 MainFrm.h 中聲明。 該範例展示如何設定圖示、設定狀態列窗格的工具提示文本、在指定窗格上顯示進度列、將動畫分配給指定的窗格、設定文本和狀態列窗格的寬度,以及設置狀態列窗格的進度列的當前進度指示器。 此代碼段是[狀態列演示範例](../../overview/visual-cpp-samples.md)的一部分。

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

**標題:** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFC狀態列::鈣固定佈局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[在]*b 伸*<br/>
[在]*布霍茲*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFC狀態列::命令索引

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

[在]*nIDFind*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFC 狀態列:建立

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

[在]*pparentwnd*<br/>
[在]*dwStyle*<br/>
[在]*nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFC 狀態列:建立Ex

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>參數

[在]*pparentwnd*<br/>
[在]*dwCtrl風格*<br/>
[在]*dwStyle*<br/>
[在]*nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFC狀態列::D允許在之前插入

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFC狀態列::啟用窗格按兩下

啟用或禁用狀態列上滑鼠按兩下的處理。

```cpp
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]如果為 TRUE,則啟用滑鼠按兩下處理。 否則禁用滑鼠雙擊處理。

### <a name="remarks"></a>備註

如果啟用狀態列處理雙擊,Windows 會在使用者按兩下狀態列窗格時將WM_COMMAND通知以及資源 ID 一起發送給狀態列的所有者。

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFC狀態列::啟用窗格進度列

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
[在]指定要啟用其進度條的窗格的索引。

*n 總計*<br/>
[在]指定進度條的最大值。

*b 顯示文字*<br/>
[在]指定進度條是否應顯示當前進度值。

*clrBar*<br/>
[在]指定進度列的背景顏色。

*克拉巴爾德斯特*<br/>
[在]指定進度條背景的輔助顏色。 使用與*clrBar*不同的值以混合到漸變的顏色填充。

*clrProgressText*<br/>
[在]指定進度條文字的顏色。

### <a name="remarks"></a>備註

如果要禁用進度列呼叫`EnablePaneProgressBar`*,nTotal*設置為 -1。 默認情況下 *,nTotal*設置為 100。 因此,您不需要任何其他計算來顯示進度(百分比)。

應為*clrBar*和*clrBarDest*傳遞不同的值,以便進度條的背景顏色顯示混合到漸變中的顏色。 .

要設置當前進度,請調用[CMFC 狀態列::設置窗格進度](#setpaneprogress)方法。

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFC狀態列:取得計數

檢索狀態列中的窗格數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

狀態列中的窗格數。

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFC 狀態列:取得 Draw 擴充區域

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFC狀態列:取得延伸區域

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>參數

[在]*rect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFC狀態列:取得項目ID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFC狀態列:取得專案已重新完成

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>
[在]*lpRect*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFC狀態列:獲取PaneInfo

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>
[在]*nID*<br/>
[在]*n樣式*<br/>
[在]*cxWidth*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFC狀態列:抓取窗格進度

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFC狀態列:抓取窗格樣式

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFC狀態列:抓取窗格文字

```cpp
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>
[在]*s*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFC狀態列:抓取窗格寬度

檢索狀態欄窗格的寬度。

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定狀態列窗格的索引。

### <a name="return-value"></a>傳回值

*nIndex*指定的狀態列窗格的寬度;否則,如果狀態列窗格不存在,則為零。

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFC 狀態列:取得提示文字

檢索狀態列窗格的工具提示文本。

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定要為其檢索工具提示文本的窗格的索引。

### <a name="return-value"></a>傳回值

*nIndex*指定的狀態列窗格的工具提示文字。 否則,如果指定的*nIndex*不存在狀態列窗格或其工具提示文本為空,則空字串。

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFC 狀態列:無效窗格內容

使狀態欄窗格無效並重繪其內容。

```cpp
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定要失效和重繪其內容的窗格的索引。

### <a name="remarks"></a>備註

當狀態欄失效時,將標記為重繪。 當方法向`UpdateWindow``OnPaint`方法發送WM_PAINT消息時,Windows 會重繪它。

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFC狀態列:在DrawPane上

重繪狀態列的窗格。

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於繪圖的設備上下文的指標。

*pPane*<br/>
[在]指向包含要重`CMFCStatusBarPaneInfo`繪的窗格資訊的結構的指標。

### <a name="remarks"></a>備註

預設情況下,`OnDrawPane`使用裝置上下文*pDC*根據窗格的樣式和內容重繪窗格。

重寫`CMFCStatusBar`派生類中的此方法以自定義窗格的外觀。

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFC狀態列::P重新建立視窗

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>參數

[在]*cs*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFC狀態列::設定 Draw 延伸區域

```cpp
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

[在]*bSet*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFC狀態列:設定指標

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

[在]*lpIDArray*<br/>
[在]*nID( N) Count*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFC狀態列:設定窗格動畫

將動畫分配給指定的窗格。

```cpp
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定要為其分配動畫的窗格的索引。

*h 影像清單*<br/>
[在]指定保存動畫幀的圖像清單的句柄。

*nFrameRate*<br/>
[在]指定動畫的幀速率(以毫秒為單位)。

*b更新*<br/>
[在]如果為 TRUE,請立即更新窗格內容。 否則,窗格內容在失效時將更新。

### <a name="remarks"></a>備註

如果要關閉當前動畫,請使用`SetPaneAnimation``hImageList`設定為 NULL 進行呼叫。

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFC狀態列:設置Pane背景顏色

設定狀態列窗格的背景顏色。

```cpp
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定為其設置新背景顏色的窗格的索引。

*clrBackground*<br/>
[在]指定新的背景顏色。

*b更新*<br/>
[在]如果為 TRUE,請立即更新窗格內容。 否則,在窗格被其他方法失效之前,不要更新窗格內容。

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFC 狀態列:設定窗格圖示

設置狀態列窗格的圖示。

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
[在]指定為其設置圖像的窗格的索引。

*hIcon*<br/>
[在]指定要設定為窗格圖像的圖示的句柄。

*b更新*<br/>
[在]指定是否立即更新窗格內容。

*hBmp*<br/>
[在]指定要設定為窗格圖像的點陣圖的句柄。

*clr透明*<br/>
[在]指定*hBmp*指示的點陣圖的透明顏色。

### <a name="remarks"></a>備註

您可以將 HICON 或 HBITMAP 與透明顏色一起傳遞以設定窗格的圖像。 如果不想再顯示圖像,則將 NULL 值作為圖像句柄傳遞。

如果[CMFC 狀態列::SetPane 動畫](#setpaneanimation)設置了任何正在運行的動畫,則動畫將停止。

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFC狀態列:設定窗格資訊

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>
[在]*nID*<br/>
[在]*n樣式*<br/>
[在]*cxWidth*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFC狀態列::設定窗格進度

為指定的窗格設置進度列的當前進度指示器。

```cpp
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定要為其更新進度指示器的窗格的索引。

*n庫爾*<br/>
[在]指定進度指示器的當前值。

*b更新*<br/>
[在]指定是否應立即更新窗格。

### <a name="remarks"></a>備註

如果要更新指定窗格中進度列的進度指示器,請調用此方法。

要對給定窗格使用此函數,必須先呼叫[CMFC 狀態列::啟用窗格進度列](#enablepaneprogressbar)。

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFC狀態列:設定窗格樣式

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>
[在]*n樣式*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFC 狀態列:設定窗格文字

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>參數

[在]*nIndex*<br/>
[在]*lpsz 新文字*<br/>
[在]*b更新*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFC 狀態列:設定窗格文字顏色

設定指定窗格的文字顏色。

```cpp
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]指定要為其分配新文字顏色的窗格的索引。

*clrText*<br/>
[在]指定文字顏色。

*b更新*<br/>
[在]如果為 TRUE,請立即更新窗格內容。 否則,在窗格被其他方法失效之前,不要更新窗格內容。

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFC狀態列:設定窗格寬度

設置狀態列窗格的寬度。

```cpp
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]要為其設置新寬度的狀態欄窗格的索引。

*殘雪*<br/>
[在]狀態欄窗格的新寬度(以像素為單位)。

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFC 狀態列:設定提示文字

設定狀態列窗格的工具提示文本。

```cpp
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]要為其分配工具提示文本的窗格的索引。

*pssTip文字*<br/>
[在]新的工具提示文字。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)
