---
title: CSplitterWnd 類別
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: a872854af1695b8b2b347b21d73165d259b3a986
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753072"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd 類別

提供分割視窗 (這是包含多個窗格的視窗) 的功能。

## <a name="syntax"></a>語法

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSplitterwnd:CSplitterwnd](#csplitterwnd)|呼叫以建構物件`CSplitterWnd`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSplitterwnd::啟動下一個](#activatenext)|執行「下一個窗格」或「上一個窗格」 命令。|
|[CSplitterwnd::可以啟動下一個](#canactivatenext)|檢查「下一個窗格」或「上一個窗格」命令當前是否可行。|
|[CSplitterwnd::創建](#create)|調用以創建一個動態拆分器視窗並將其附加到`CSplitterWnd`物件。|
|[CSplitterwnd::創建ScrollBarCtrl](#createscrollbarctrl)|創建共用滾動條控制項。|
|[CSplitterwnd::創建靜態](#createstatic)|調用以創建靜態拆分器視窗並將其附加到`CSplitterWnd`物件。|
|[CSplitterwnd::創建檢視](#createview)|呼叫以在分割器視窗中創建窗格。|
|[CSplitterwnd::DeleteColumn](#deletecolumn)|從分割器視窗中移除欄。|
|[CSplitterwnd::DeleteRow](#deleterow)|從分割器視窗中移除行。|
|[CSplitterwnd::Delete查看](#deleteview)|從分割器視窗中刪除檢視。|
|[CSplitterwnd::Do鍵盤拆分](#dokeyboardsplit)|執行鍵盤拆分命令,通常為"視窗拆分"。|
|[CSplitterwnd::DoScroll](#doscroll)|對分割視窗執行同步滾動。|
|[CSplitterwnd::DoScrollBy](#doscrollby)|按給定像素數滾動拆分視窗。|
|[CSplitterwnd::獲取活動窗格](#getactivepane)|從框架中的焦點檢視或活動檢視中確定活動窗格。|
|[CSplitterwnd::獲取縱隊計數](#getcolumncount)|返回當前窗格列計數。|
|[CSplitterwnd::獲取縱隊資訊](#getcolumninfo)|返回指定列上的資訊。|
|[CSplitterwnd::GetPane](#getpane)|返回指定行和列處的窗格。|
|[CSplitterwnd::獲取羅計數](#getrowcount)|返回當前窗格行計數。|
|[CSplitterwnd::獲取羅資訊](#getrowinfo)|返回指定行上的資訊。|
|[CSplitterwnd::獲取滾動樣式](#getscrollstyle)|返回共享滾動條樣式。|
|[CSplitterwnd::IdFromRowCol](#idfromrowcol)|在指定的行和列上傳回窗格的子視窗 ID。|
|[CSplitterwnd::IsChildPane](#ischildpane)|呼叫以確定視窗目前是否是此拆分器視窗的子窗格。|
|[CSplitterwnd:正在追蹤](#istracking)|確定當前是否正在移動拆分條。|
|[CSplitterwnd:recalclayout](#recalclayout)|在調整列或列大小後調用以重新顯示分割器視窗。|
|[CSplitterwnd::設定活動窗格](#setactivepane)|將窗格設為框架中的活動窗格。|
|[CSplitterwnd::SetColumninfo](#setcolumninfo)|調用以設置指定的列資訊。|
|[CSplitterwnd::SetRowInfo](#setrowinfo)|調用以設置指定的行資訊。|
|[CSplitterwnd::設置滾動樣式](#setscrollstyle)|為拆分器視窗的共用滾動條支援指定新的滾動條樣式。|
|[CSplitterwnd::拆分柱](#splitcolumn)|指示框架視窗垂直拆分的位置。|
|[CSplitterwnd::拆分行](#splitrow)|指示框架視窗水準拆分的位置。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CSplitterwnd::OnDraw](#ondraw)|由框架調用以繪製拆分器視窗。|
|[CSplitterwnd::在牽引器上](#ondrawsplitter)|渲染拆分視窗的圖像。|
|[CSplitterwnd::上反轉追蹤器](#oninverttracker)|渲染拆分視窗的圖像的大小和形狀與框架視窗相同。|

## <a name="remarks"></a>備註

窗格通常是從[CView](../../mfc/reference/cview-class.md)派生的應用程式特定物件,但它可以是具有適當子視窗 ID 的任何[CWnd](../../mfc/reference/cwnd-class.md)物件。

物件`CSplitterWnd`通常嵌入在父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildwnd](../../mfc/reference/cmdichildwnd-class.md)物件中。 使用以下步驟`CSplitterWnd`建立物件:

1. 在`CSplitterWnd`父幀中嵌入成員變數。

2. 覆蓋父幀的[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函數。

3. 從重寫`OnCreateClient`中,呼`CSplitterWnd`叫的[創建](#create)或[創建靜態](#createstatic)成員函數。

調用`Create`成員函數以創建動態拆分器視窗。 動態拆分器視窗通常用於創建和滾動同一文檔的多個單個窗格或視圖。 框架會自動為分割器創建初始窗格;但是,框架會自動為分割器創建一個初始窗格。然後,當使用者操作拆分器視窗的控制項時,框架將創建、調整和釋放其他窗格。

呼叫`Create`時 ,指定最小行高度和列寬度,以確定窗格何時太小而無法完全顯示。 呼叫`Create`後,可以透過調用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函數來調整這些最小值。

還使用`SetColumnInfo``SetRowInfo`和成員函數為列設置"理想"寬度,為行設置"理想"高度。 當框架顯示分割器視窗時,它首先顯示父框架,然後顯示拆分器視窗。 然後,框架根據它們的理想尺寸以列和行的形式排列窗格,從拆分視窗工作區的左上角到右下角工作。

動態拆分器視窗中的所有窗格必須屬於同一類。 支援動態拆分視窗的熟悉應用程式包括 Microsoft Word 和 Microsoft Excel。

使用`CreateStatic`成員函數創建靜態拆分器視窗。 使用者只能更改靜態拆分器視窗中窗格的大小,而不能更改其數量或順序。

建立靜態拆分器時,必須專門創建所有靜態拆分器的窗格。 請確保在父框架`OnCreateClient`的成員函數返回之前創建所有窗格,否則框架將不能正確顯示視窗。

成員`CreateStatic`函數自動初始化最小行高度和列寬度為 0 的靜態拆分器。 呼叫`Create`後,透過調用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函數來調整這些最小值。 還使用`SetColumnInfo`和`SetRowInfo`調用`CreateStatic`後指示所需的理想窗格尺寸。

靜態拆分器的各個窗格通常屬於不同的類。 有關靜態拆分視窗的範例,請參閱圖形編輯器和 Windows 檔案管理器。

拆分視窗支援特殊的滾動條(除了窗格可能具有的滾動條)。 這些滾動條是物件的子級`CSplitterWnd`,並與窗格共用。

建立分割視窗時,可以創建這些特殊的滾動條。 例如,具有一`CSplitterWnd`行、兩列和WS_VSCROLL樣式的將顯示由兩個窗格共用的垂直滾動條。 當使用者移動滾動條時,WM_VSCROLL消息發送到兩個窗格。 當窗格設置滾動條位置時,將設置共用滾動條。

有關拆分視窗的詳細資訊,請參閱[技術說明 29](../../mfc/tn029-splitter-windows.md)。

有關如何創建動態拆分器視窗的詳細資訊,請參閱:

- MFC 樣品[塗鴉](../../overview/visual-cpp-samples.md)

- MFC 樣品[VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterwnd::啟動下一個

由框架呼叫以執行下一個窗格或「上一個窗格」 命令。

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>參數

*bPrev*<br/>
指示要啟動的視窗。 **以前的 TRUE;****下一個為 FALSE。**

### <a name="remarks"></a>備註

此成員函數是[CView](../../mfc/reference/cview-class.md)類用來委派到實現`CSplitterWnd`的高級 命令。

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterwnd::可以啟動下一個

由框架呼叫以檢視目前是否可以使用「下一個窗格」或「上一個窗格」 命令。

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>參數

*bPrev*<br/>
指示要啟動的視窗。 **以前的 TRUE;****下一個為 FALSE。**

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數是[CView](../../mfc/reference/cview-class.md)類用來委派到實現`CSplitterWnd`的高級 命令。

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterwnd::創建

要建立動態分割器視窗,`Create`請呼叫成員函數。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
拆分器視窗的父框架視窗。

*nMaxRows*<br/>
分割器視窗中的最大行數。 此值不得超過 2。

*nMaxCols*<br/>
分割器視窗中的最大欄數。 此值不得超過 2。

*大小明*<br/>
指定窗格可以顯示的最小大小。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。 在大多數情況下,這可以是傳遞給父幀視窗的*pContext。*

*dwStyle*<br/>
指定視窗樣式。

*nID*<br/>
視窗的子視窗 ID。 除非拆分器視窗嵌套在另一個拆分器視窗中,否則可以AFX_IDW_PANE_FIRST ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以透過執行以下步驟`CSplitterWnd`將 嵌入父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildwnd](../../mfc/reference/cmdichildwnd-class.md)物件:

1. 在`CSplitterWnd`父幀中嵌入成員變數。

1. 覆蓋父幀的[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函數。

1. 從重寫`Create``OnCreateClient`中調用成員函數。

從父幀內創建拆分視窗時,將父幀的*pContext*參數傳遞給拆分器視窗。 否則,此參數可以是 NULL。

動態拆分器視窗的初始最小行高度和列寬度由*sizeMin*參數設置。 這些最小值決定了窗格是否太小而無法完整顯示,可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函數進行更改。

有關動態分割視窗的詳細資訊,請參閱文章[「多個文檔類型」、「視圖」和「框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)」、「[技術說明 29」](../../mfc/tn029-splitter-windows.md)和`CSplitterWnd`「類概述」中的「拆分視窗」。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterwnd::創建ScrollBarCtrl

由框架調用以創建共用滾動條控制項。

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定視窗樣式。

*nID*<br/>
視窗的子視窗 ID。 除非拆分器視窗嵌套在另一個拆分器視窗中,否則可以AFX_IDW_PANE_FIRST ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

覆蓋`CreateScrollBarCtrl`以在滾動條旁邊包含額外的控制項。 默認行為是創建正常的 Windows 滾動條控制項。

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterwnd::創建靜態

要建立靜態分割器視窗,`CreateStatic`請呼叫成員函數。

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
拆分器視窗的父框架視窗。

*nRows*<br/>
資料列數目。 此值不得超過 16。

*n科爾斯*<br/>
資料行數目。 此值不得超過 16。

*dwStyle*<br/>
指定視窗樣式。

*nID*<br/>
視窗的子視窗 ID。 除非拆分器視窗嵌套在另一個拆分器視窗中,否則可以AFX_IDW_PANE_FIRST ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

通常`CSplitterWnd`透過執行以下步驟嵌入`CFrameWnd`父 物件或[CMDIChildwnd](../../mfc/reference/cmdichildwnd-class.md)物件中:

1. 在`CSplitterWnd`父幀中嵌入成員變數。

1. 覆蓋父幀的成員`OnCreateClient`函數。

1. 從重寫`CreateStatic`的 CFrameWnd 中呼叫成員函數[::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。

靜態拆分器視窗包含固定數量的窗格,通常來自不同的類。

建立靜態拆分器視窗時,必須同時創建其所有窗格。 [CreateView](#createview)成員函數通常用於此目的,但您也可以創建其他非檢視類。

靜態拆分器視窗的初始最小行高度和列寬度為 0。 這些最小值決定了窗格何時太小而無法完整顯示,可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函數進行更改。

要將捲軸移至靜態分割器視窗,請將WS_HSCROLL和WS_VSCROLL樣式加入*到 dwStyle*。

有關靜態拆分器視窗的詳細資訊,請參閱文章"[多個文件類型、視圖和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技術說明 29"](../../mfc/tn029-splitter-windows.md)中的`CSplitterWnd`「拆分視窗」。

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterwnd::創建檢視

為靜態拆分器視窗創建窗格。

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

*列*<br/>
指定放置新檢視的分割器視窗列。

*col*<br/>
指定放置新檢視的分割器視窗列。

*pView 類別*<br/>
指定新檢視的[CRuntimeClass。](../../mfc/reference/cruntimeclass-structure.md)

*尺寸 Init*<br/>
指定新檢視的初始大小。

*pContext*<br/>
指向創建上下文的指標,用於創建檢視(通常*pContext*傳遞到父幀的重寫[CFrameWnd::onCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函數,其中正在創建分割器視窗)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

在框架顯示分割器之前,必須創建靜態拆分器視窗的所有窗格。

當動態拆分器視窗的使用者拆分窗格、行或列時,框架還會調用此成員函數創建新窗格。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterwnd:CSplitterwnd

呼叫以建構物件`CSplitterWnd`。

```
CSplitterWnd();
```

### <a name="remarks"></a>備註

分兩`CSplitterWnd`步構造物件。 首先調用建構函數,該建構函數創建`CSplitterWnd`物件,然後調用[Create](#create)成員函數,該函數創建拆分器視窗並將`CSplitterWnd`其附加到 物件。

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterwnd::DeleteColumn

從分割器視窗中移除欄。

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>參數

*colDelete*<br/>
指定要刪除的欄。

### <a name="remarks"></a>備註

框架調用此成員函數以實現動態拆分器視窗的邏輯(即,如果拆分器視窗具有SPLS_DYNAMIC_SPLIT樣式)。 它可以與虛擬函數[CreateView](#createview)一起自定義,以實現更進階的動態拆分器。

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterwnd::DeleteRow

從分割器視窗中移除行。

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>參數

*列刪除*<br/>
指定要刪除的行。

### <a name="remarks"></a>備註

框架調用此成員函數以實現動態拆分器視窗的邏輯(即,如果拆分器視窗具有SPLS_DYNAMIC_SPLIT樣式)。 它可以與虛擬函數[CreateView](#createview)一起自定義,以實現更進階的動態拆分器。

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterwnd::Delete查看

從分割器視窗中刪除檢視。

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>參數

*列*<br/>
指定要刪除檢視的分割器視窗列。

*col*<br/>
指定要刪除檢視的分割器視窗列。

### <a name="remarks"></a>備註

如果正在刪除活動檢視,則下一個檢視將變為活動狀態。 預設以顯示的檢視, 將在[PostNc 銷毀](../../mfc/reference/cwnd-class.md#postncdestroy)中自動刪除 。

框架調用此成員函數以實現動態拆分器視窗的邏輯(即,如果拆分器視窗具有SPLS_DYNAMIC_SPLIT樣式)。 它可以與虛擬函數[CreateView](#createview)一起自定義,以實現更進階的動態拆分器。

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterwnd::Do鍵盤拆分

執行鍵盤拆分命令,通常為"視窗拆分"。

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數是[CView](../../mfc/reference/cview-class.md)類用來委派到實現`CSplitterWnd`的高級 命令。

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterwnd::DoScroll

對分割視窗執行同步滾動。

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*pView 從*<br/>
指向滾動消息源自的視圖的指標。

*nScrollCode*<br/>
指示使用者滾動請求的滾動條代碼。 此參數由兩部分組成:一個低階位元組,它確定水準發生的滾動類型;高階位元組,確定垂直發生的滾動類型:

- SB_BOTTOM滾動到底部。

- SB_LINEDOWN向下滾動一行。

- SB_LINEUP向上滾動一行。

- SB_PAGEDOWN向下滾動一頁。

- SB_PAGEUP向上滾動一頁。

- SB_TOP滾動到頂部。

*b多卷*<br/>
確定是否執行指定的滾動操作。 如果*bDoScroll*為 TRUE(即,如果存在子視窗,並且拆分視窗具有滾動範圍),則可以執行指定的滾動操作;如果存在子視窗,則可以執行指定的滾動操作。如果*bDoScroll*是 FALSE(即,如果不存在子視窗,或者拆分視圖沒有滾動範圍),則不會發生滾動。

### <a name="return-value"></a>傳回值

如果同步滾動發生,則非零;否則 0。

### <a name="remarks"></a>備註

框架將調用此成員函數,在視圖收到滾動消息時執行拆分視窗的同步滾動。 在允許同步滾動之前,需要用戶執行操作。

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterwnd::DoScrollBy

按給定像素數滾動拆分視窗。

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*pView 從*<br/>
指向滾動消息源自的視圖的指標。

*大小捲動*<br/>
要水準和垂直滾動的圖元數。

*b多卷*<br/>
確定是否執行指定的滾動操作。 如果*bDoScroll*為 TRUE(即,如果存在子視窗,並且拆分視窗具有滾動範圍),則可以執行指定的滾動操作;如果存在子視窗,則可以執行指定的滾動操作。如果*bDoScroll*是 FALSE(即,如果不存在子視窗,或者拆分視圖沒有滾動範圍),則不會發生滾動。

### <a name="return-value"></a>傳回值

如果同步滾動發生,則非零;否則 0。

### <a name="remarks"></a>備註

框架調用此成員函數以回應滾動訊息,以按*大小Scroll*指示的數量(以像素為單位)對拆分視窗執行同步滾動。 正值表示向下和向右滾動;負值表示向上和向左滾動。

在允許滾動之前,重寫以需要用戶執行操作。

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterwnd::獲取活動窗格

從框架中的焦點檢視或活動檢視中確定活動窗格。

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>參數

*pRow*<br/>
指向**int**的指標,用於檢索活動窗格的行號。

*pCol*<br/>
指向**int**的指標,用於檢索活動窗格的列號。

### <a name="return-value"></a>傳回值

指向活動窗格的指標。 如果沒有活動窗格,則 NULL。

### <a name="remarks"></a>備註

框架調用此成員函數以確定分割器視窗中的活動窗格。 在獲取活動窗格之前,重寫以需要使用者執行操作。

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterwnd::獲取縱隊計數

返回當前窗格列計數。

```
int GetColumnCount() const;
```

### <a name="return-value"></a>傳回值

返回分割器中的當前列數。 對於靜態拆分器,這也將是列的最大數量。

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterwnd::獲取縱隊資訊

返回指定列上的資訊。

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>參數

*col*<br/>
指定資料行。

*cxCur*<br/>
要設置為列的當前寬度的**int**的引用。

*cxMin*<br/>
要設置為列的當前最小寬度的**int**的引用。

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterwnd::GetPane

返回指定行和列處的窗格。

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>參數

*列*<br/>
指定行。

*col*<br/>
指定資料行。

### <a name="return-value"></a>傳回值

返回指定行和列處的窗格。 返回的窗格通常是[CView](../../mfc/reference/cview-class.md)派生類。

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterwnd::獲取羅計數

返回當前窗格行計數。

```
int GetRowCount() const;
```

### <a name="return-value"></a>傳回值

返回分割器視窗中的當前行數。 對於靜態拆分器視窗,這也將是最大行數。

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterwnd::獲取羅資訊

返回指定行上的資訊。

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>參數

*列*<br/>
指定行。

*cyCur*<br/>
要設置為以像素為單位的行的當前高度的**int**的引用。

*賽明*<br/>
要設置為以像素為單位的行的當前最小高度的**int**的引用。

### <a name="remarks"></a>備註

調用此成員函數以獲取有關指定行的資訊。 *cyCur*參數用指定行的當前高度填充 *,cyMin*填充該行的最小高度。

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterwnd::獲取滾動樣式

返回拆分器視窗的共用滾動條樣式。

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>傳回值

如果成功,則一個或多個以下視窗樣式標誌:

- WS_HSCROLL 如果拆分器當前管理共用水平滾動條。

- WS_VSCROLL 如果拆分器當前管理共用垂直滾動條。

如果為零,拆分器視窗當前不管理任何共用滾動條。

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterwnd::IdFromRowCol

取得指定列和列窗格的子視窗 ID。

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>參數

*列*<br/>
指定分割器視窗列。

*col*<br/>
指定分割器視窗列。

### <a name="return-value"></a>傳回值

窗格的子視窗 ID。

### <a name="remarks"></a>備註

此成員函數用於將非檢視創建為窗格,並可能在窗格存在之前調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterwnd::IsChildPane

確定*pWnd*目前是否是此拆分器視窗的子窗格。

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向要測試的[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

*pRow*<br/>
指向要在其中存儲行號的**int**的指標。

*pCol*<br/>
指向用於存儲列編號的**int**的指標。

### <a name="return-value"></a>傳回值

如果為非零 *,pWnd*當前是此拆分器視窗的子窗格 *,pRow*和*pCol*中填充了拆分器視窗中窗格的位置。 如果*pWnd*不是此拆分器視窗的子窗格,則返回 0。

### <a name="remarks"></a>備註

在 6.0 之前的 Visual C++ 版本中,此函數定義為

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

此版本現已過時,不應使用。

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterwnd:正在追蹤

呼叫此成員函數以確定視窗中的拆分器條當前是否正在移動。

```
BOOL IsTracking();
```

### <a name="return-value"></a>傳回值

如果拆分器操作正在進行,則非零;否則 0。

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterwnd::在牽引器上

渲染拆分視窗的圖像。

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向要繪製的設備上下文的指標。 如果*pDC*為 NULL,則框架將調用[CWnd::redrawWindow,](../../mfc/reference/cwnd-class.md#redrawwindow)並且不繪製拆分視窗。

*nType*<br/>
的值`enum ESplitType`可以是以下值之一:

- `splitBox`拆分器拖動框。

- `splitBar`出現在兩個拆分視窗之間的條形。

- `splitIntersection`拆分視窗的交點。 在 Windows 95/98 上運行時,不會調用此元素。

- `splitBorder`拆分視窗邊框。

*矩形*<br/>
對[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的引用,指定分割視窗的大小和形狀。

### <a name="remarks"></a>備註

框架調用此成員函數以繪製和指定拆分器視窗的確切特徵。 覆蓋`OnDrawSplitter`以進階自訂分割器視窗的各種圖形元件的圖像。 默認影像類似於適用於 Windows 的 Microsoft Works 或 Microsoft Windows 95/98 中的拆分器,因為拆分器條的交點混合在一起。

有關動態分割視窗的詳細資訊,請參閱文章[「多個文檔類型」、「視圖」和「框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)」、「[技術說明 29」](../../mfc/tn029-splitter-windows.md)和`CSplitterWnd`「類概述」中的「拆分視窗」。

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterwnd::上反轉追蹤器

渲染拆分視窗的圖像的大小和形狀與框架視窗相同。

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>參數

*矩形*<br/>
引用指定追蹤`CRect`矩形的物件。

### <a name="remarks"></a>備註

在調整拆分器大小時,框架將調用此成員函數。 覆蓋`OnInvertTracker`以先進自訂拆分器視窗的圖像。 默認影像類似於適用於 Windows 的 Microsoft Works 或 Microsoft Windows 95/98 中的拆分器,因為拆分器條的交點混合在一起。

有關動態分割視窗的詳細資訊,請參閱文章[「多個文檔類型」、「視圖」和「框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)」、「[技術說明 29」](../../mfc/tn029-splitter-windows.md)和`CSplitterWnd`「類概述」中的「拆分視窗」。

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterwnd:recalclayout

在調整列或列大小後調用以重新顯示分割器視窗。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函數調整行和列大小後,呼叫此成員函數以正確重新顯示拆分器視窗。 如果在分割器視窗可見之前更改行和列大小作為創建過程的一部分,則不必呼叫此成員函數。

每當用戶調整分割視窗的大小或移動拆分時,框架都會調用此成員函數。

### <a name="example"></a>範例

  請參閱[CSplitterWnd 的範例::SetColumnInfo](#setcolumninfo)。

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterwnd::設定活動窗格

將窗格設為框架中的活動窗格。

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>參數

*列*<br/>
如果*pWnd*為 NULL,則指定窗格中將處於活動狀態的行。

*col*<br/>
如果*pWnd*為 NULL,則指定窗格中將處於活動狀態的列。

*pwnd*<br/>
`CWnd` 物件的指標。 如果為 NULL,*則行*和*col*指定的窗格將設置為活動。 如果不是 NULL,則指定設定為活動的窗格。

### <a name="remarks"></a>備註

當使用者將焦點更改為框架視窗中的窗格時,框架將此成員函數設置為活動窗格。 您可以顯式調用`SetActivePane`以將焦點更改為指定的檢視。

通過提供行和列 **,或通過**提供*pWnd*來指定窗格。

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterwnd::SetColumninfo

調用以設置指定的列資訊。

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>參數

*col*<br/>
指定分割器視窗列。

*cx理想*<br/>
指定以像素為單位的拆分視窗列的理想寬度。

*cxMin*<br/>
指定以像素為單位的拆分視窗列的最小寬度。

### <a name="remarks"></a>備註

調用此成員函數以設置列的新最小寬度和理想寬度。 列最小值確定列何時太小而無法完全顯示。

當框架顯示分割器視窗時,它會根據它們的理想尺寸以列和行的形式排列窗格,從拆分視窗工作區的左上角到右下角工作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterwnd::SetRowInfo

調用以設置指定的行資訊。

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>參數

*列*<br/>
指定分割視窗列。

*賽理想*<br/>
指定以像素為單位的拆分視窗行的理想高度。

*賽明*<br/>
指定以像素為單位的拆分視窗行的最小高度。

### <a name="remarks"></a>備註

調用此成員函數以為行設置新的最小高度和理想高度。 行最小值確定行何時太小而無法完全顯示。

當框架顯示分割器視窗時,它會根據它們的理想尺寸以列和行的形式排列窗格,從拆分視窗工作區的左上角到右下角工作。

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterwnd::設置滾動樣式

指定分割視窗的共用滾動條支援的新滾動樣式。

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
分割視窗的分享滾動條支援的新滾動樣式,可以是以下值之一:

- WS_HSCROLL 創建/顯示水平共用滾動條。

- WS_VSCROLL 創建/顯示垂直共用滾動條。

### <a name="remarks"></a>備註

創建滾動條后,即使調用沒有該樣式`SetScrollStyle`,也不會銷毀它;相反,這些滾動條是隱藏的。 這允許滾動條保留其狀態,即使它們處於隱藏狀態。 呼叫`SetScrollStyle`後,必須調用[RecalcLayout,](#recalclayout)以便所有更改生效。

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterwnd::拆分柱

指示框架視窗垂直拆分的位置。

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>參數

*cx 之前*<br/>
發生拆分的位置(以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

創建垂直拆分器視窗時,將調用此成員函數。 `SplitColumn`指示發生拆分的預設位置。

`SplitColumn`框架調用實現動態拆分器視窗的邏輯(即,如果拆分器視窗具有SPLS_DYNAMIC_SPLIT樣式)。 它可以與虛擬函數[CreateView](#createview)一起自定義,以實現更進階的動態拆分器。

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterwnd::拆分行

指示框架視窗水準拆分的位置。

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>參數

*cy 之前*<br/>
發生拆分的位置(以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

創建水準拆分器視窗時,將調用此成員函數。 `SplitRow`指示發生拆分的預設位置。

`SplitRow`框架調用實現動態拆分器視窗的邏輯(即,如果拆分器視窗具有SPLS_DYNAMIC_SPLIT樣式)。 它可以與虛擬函數[CreateView](#createview)一起自定義,以實現更進階的動態拆分器。

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterwnd::OnDraw

由框架調用以繪製拆分器視窗。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
裝置內容的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[MFC 樣品檢視](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
