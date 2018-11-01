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
ms.openlocfilehash: 450699d001ee7246742fe23d9bf89d03c2d61cb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600504"
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
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|呼叫來建構`CSplitterWnd`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|執行下一個窗格或上一個窗格的命令。|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|檢查是否為目前的下一個窗格或上一個窗格的命令。|
|[CSplitterWnd::Create](#create)|若要建立動態分隔視窗，並將其附加至呼叫`CSplitterWnd`物件。|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|建立共用的捲軸控制項。|
|[CSplitterWnd::CreateStatic](#createstatic)|若要建立靜態分隔視窗，並將其附加至呼叫`CSplitterWnd`物件。|
|[CSplitterWnd::CreateView](#createview)|呼叫以建立在分隔器視窗的窗格。|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|從分隔器視窗刪除一個資料行。|
|[CSplitterWnd::DeleteRow](#deleterow)|從分隔器視窗刪除一個資料列。|
|[CSplitterWnd::DeleteView](#deleteview)|從分隔器視窗刪除一個檢視。|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|執行鍵盤分隔的命令，通常是 「 視窗分割 」。|
|[CSplitterWnd::DoScroll](#doscroll)|執行同步的分隔視窗捲動。|
|[CSplitterWnd::DoScrollBy](#doscrollby)|捲動分隔視窗的指定像素數目。|
|[CSplitterWnd::GetActivePane](#getactivepane)|判斷焦點或框架中的現用檢視表從 [作用中] 窗格。|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|傳回目前的窗格中的資料行計數。|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|傳回指定的資料行的相關資訊。|
|[CSplitterWnd::GetPane](#getpane)|傳回在指定的資料列和資料行的窗格。|
|[CSplitterWnd::GetRowCount](#getrowcount)|傳回目前的窗格中的資料列計數。|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|傳回指定的資料列的相關資訊。|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|傳回共用的捲軸樣式。|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|傳回子視窗窗格中，在指定的資料列和資料行識別碼。|
|[CSplitterWnd::IsChildPane](#ischildpane)|若要判斷視窗是否目前是子窗格中的這個分隔器視窗呼叫。|
|[CSplitterWnd::IsTracking](#istracking)|決定是否分割列目前正在移動。|
|[CSplitterWnd::RecalcLayout](#recalclayout)|若要重新分隔器視窗顯示調整資料列或資料行的大小之後呼叫。|
|[CSplitterWnd::SetActivePane](#setactivepane)|將框架中作用中的一個窗格的設定。|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|呼叫以設定指定的資料行資訊。|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|呼叫來設定指定的資料列的資訊。|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|指定新的捲軸樣式分隔器視窗共用捲軸的支援。|
|[CSplitterWnd::SplitColumn](#splitcolumn)|指示框架視窗垂直分隔的位置為何。|
|[CSplitterWnd::SplitRow](#splitrow)|指示框架視窗水平分割的位置。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|由架構呼叫以繪製分隔器視窗。|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|呈現分隔視窗的影像。|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|呈現分隔視窗是相同的大小和形狀與框架視窗的影像。|

## <a name="remarks"></a>備註

窗格通常是應用程式特定物件衍生自[CView](../../mfc/reference/cview-class.md)，但它可以是任何[CWnd](../../mfc/reference/cwnd-class.md)物件，具有適當的子視窗識別碼。

A`CSplitterWnd`物件通常內嵌在父代[CFrameWnd](../../mfc/reference/cframewnd-class.md)或是[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件。 建立`CSplitterWnd`物件使用下列步驟：

1. 內嵌`CSplitterWnd`父框架中的成員變數。

2. 覆寫父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。

3. 從內覆寫`OnCreateClient`，呼叫[建立](#create)或是[CreateStatic](#createstatic)成員函式`CSplitterWnd`。

呼叫`Create`成員函式來建立動態分隔視窗。 動態分隔視窗通常用來建立及捲動數個個別的窗格或檢視相同文件。 架構會自動建立初始的窗格分隔器;然後架構會建立、 調整大小，並處置的其他窗格中，與使用者分隔器視窗的控制項。

當您呼叫`Create`，指定最小資料列高度和資料行寬度，以決定何時太小，無法完全顯示的窗格。 在您呼叫後`Create`，您可以調整的最小值，藉由呼叫[SetColumnInfo](#setcolumninfo)並[SetRowInfo](#setrowinfo)成員函式。

也使用`SetColumnInfo`和`SetRowInfo`成員函式，以設定 「 理想 」 的資料行寬度] 和 [「 理想 」 的資料列的高度。 時，架構會顯示分隔器視窗，它首先會顯示父框架，然後分隔器視窗。 架構接著會配置資料行和資料列，根據其理想的維度，使用從左上角到右下角的分隔器視窗的工作區中的窗格。

動態分隔視窗中的所有窗格都必須屬於相同的類別。 熟悉支援動態分隔視窗的應用程式包括 Microsoft Word 和 Microsoft Excel。

使用`CreateStatic`成員函式來建立靜態分隔視窗。 使用者可以變更 [靜態分隔器視窗，其數目或順序不使用中] 窗格的大小。

具體來說，當您建立靜態分隔器時，您必須建立所有靜態分割的窗格。 請確定您建立父框架之前的所有窗格`OnCreateClient`成員函式傳回的物件或 framework 將無法正確顯示視窗。

`CreateStatic`成員函式會自動初始化靜態分隔器最小資料列高度和資料行寬度是 0。 在您呼叫後`Create`，調整的最小值，藉由呼叫[SetColumnInfo](#setcolumninfo)並[SetRowInfo](#setrowinfo)成員函式。 也使用`SetColumnInfo`並`SetRowInfo`在您呼叫後`CreateStatic`表示需要 [理想] 窗格的維度。

靜態分隔器的個別窗格通常屬於不同類別。 如需靜態分隔視窗的範例，請參閱圖形編輯器和 Windows 檔案管理員。

分隔器視窗支援 （除了窗格可能會有捲軸） 的特殊的捲軸。 這些捲軸是子系`CSplitterWnd`物件，並與窗格共用。

當您建立分隔器視窗時，您會建立這些特殊的捲軸。 比方說，`CSplitterWnd`具有一個資料列、 兩個資料行，且 WS_VSCROLL 樣式會顯示垂直捲軸所共用的兩個窗格。 當使用者移動捲軸時，WM_VSCROLL 訊息會傳送至這兩個窗格。 當窗格設定捲軸位置時，會設定共用的捲軸。

如需分隔視窗的詳細資訊，請參閱[技術的附註 29](../../mfc/tn029-splitter-windows.md)。

如需有關如何建立動態分隔視窗的詳細資訊，請參閱：

- MFC 範例[Scribble](../../visual-cpp-samples.md)

- MFC 範例[VIEWEX](../../visual-cpp-samples.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext

由架構呼叫以執行下一個窗格或上一個窗格的命令。

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>參數

*bPrev*<br/>
表示要啟用哪一個視窗。 **TRUE**的上一個;**FALSE**的下一步。

### <a name="remarks"></a>備註

此成員函式是高層級的命令，以供[CView](../../mfc/reference/cview-class.md)類別來委派給`CSplitterWnd`實作。

##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext

由架構呼叫以查看是否有下一個窗格或上一個窗格的命令目前無法檢查。

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>參數

*bPrev*<br/>
表示要啟用哪一個視窗。 **TRUE**的上一個;**FALSE**的下一步。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式是高層級的命令，以供[CView](../../mfc/reference/cview-class.md)類別來委派給`CSplitterWnd`實作。

##  <a name="create"></a>  CSplitterWnd::Create

若要建立動態分隔視窗，呼叫`Create`成員函式。

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

*pParentWnd*<br/>
分隔器視窗父框架視窗。

*nMaxRows*<br/>
在分隔器視窗中的資料列的數目上限。 此值不可超過 2。

*nMaxCols*<br/>
在分隔器視窗中的資料行數目上限。 此值不可超過 2。

*sizeMin*<br/>
指定的最小的可能執行的動作會顯示一個窗格。

*pContext*<br/>
指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 在大部分情況下，這可以是*pContext*傳遞給父框架視窗。

*cheaderctrl:: Create*<br/>
指定的視窗樣式。

*nID*<br/>
視窗的子視窗識別碼。 識別碼可以是 AFX_IDW_PANE_FIRST，除非在另一個分隔器視窗中的分隔器視窗為巢狀。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以將內嵌`CSplitterWnd`父系[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件採取下列步驟：

1. 內嵌`CSplitterWnd`父框架中的成員變數。

1. 覆寫父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。

1. 呼叫`Create`成員函式內覆寫`OnCreateClient`。

當您建立從分隔器視窗父範圍內時，傳遞父框架*pContext*參數，以分隔器視窗。 否則，這個參數可以是 NULL。

動態分隔視窗的初始最小的資料列高度和資料行寬度由設定*sizeMin*參數。 這些最小值，判斷是否為太小，無法顯示完整的窗格中，可以變更[SetRowInfo](#setrowinfo)並[SetColumnInfo](#setcolumninfo)成員函式。

如需動態分隔視窗的詳細資訊，請參閱 」 分隔器 Windows 」 一文中[多個文件類型、 檢視和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`類別概觀。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl

由架構呼叫以建立共用的捲軸控制項。

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
指定的視窗樣式。

*nID*<br/>
視窗的子視窗識別碼。 識別碼可以是 AFX_IDW_PANE_FIRST，除非在另一個分隔器視窗中的分隔器視窗為巢狀。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

覆寫`CreateScrollBarCtrl`包括額外的控制項旁的捲軸。 預設行為是建立一般 Windows 捲軸控制項。

##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic

若要建立靜態分隔視窗，呼叫`CreateStatic`成員函式。

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
分隔器視窗父框架視窗。

*nRows*<br/>
列的數目。 此值不可超過 16。

*nCols*<br/>
行數。 此值不可超過 16。

*cheaderctrl:: Create*<br/>
指定的視窗樣式。

*nID*<br/>
視窗的子視窗識別碼。 識別碼可以是 AFX_IDW_PANE_FIRST，除非在另一個分隔器視窗中的分隔器視窗為巢狀。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

A`CSplitterWnd`通常會內嵌在父代`CFrameWnd`或是[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件採取下列步驟：

1. 內嵌`CSplitterWnd`父框架中的成員變數。

1. 覆寫父框架`OnCreateClient`成員函式。

1. 呼叫`CreateStatic`成員函式內覆寫[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。

靜態分隔視窗包含固定的數目的窗格，通常是從不同的類別。

當您建立靜態分隔視窗時，您必須在同一時間建立所有窗格。 [CreateView](#createview)成員函式通常用於此目的，但您可以建立其他 nonview 類別。

靜態分隔視窗的初始最小的資料列高度和資料行寬度是 0。 這些最小值，判斷太小而無法完整顯示一個窗格時，可以變更[SetRowInfo](#setrowinfo)並[SetColumnInfo](#setcolumninfo)成員函式。

若要加入靜態分隔視窗的捲軸，新增的 WS_HSCROLL 和 WS_VSCROLL 樣式*cheaderctrl:: Create*。

一文中看到 「 分隔器 Windows 」[多個文件類型、 檢視和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`類別概觀，如需靜態分隔視窗的詳細資訊。

##  <a name="createview"></a>  CSplitterWnd::CreateView

建立靜態分隔視窗的窗格。

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

*資料列*<br/>
指定分隔器視窗資料列，在其中放置新的檢視。

*資料行*<br/>
指定分隔器視窗資料行，在其中放置新的檢視。

*pViewClass*<br/>
指定[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)新的檢視。

*sizeInit*<br/>
指定新的檢視表的初始大小。

*pContext*<br/>
建立內容，用來建立檢視的指標 (通常*pContext*傳遞至父框架的覆寫[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)分隔器視窗的成員函式正在建立）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

必須先建立所有的靜態分隔視窗的窗格，架構會顯示為分隔器。

架構也會呼叫此成員函式，建立新的窗格，窗格中，資料列或資料行，會將分割動態分隔視窗的使用者時。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd

呼叫來建構`CSplitterWnd`物件。

```
CSplitterWnd();
```

### <a name="remarks"></a>備註

建構`CSplitterWnd`兩個步驟中的物件。 首先，呼叫建構函式，這會建立`CSplitterWnd`物件，然後再呼叫[建立](#create)成員函式，會建立分隔器視窗，並將它附加至`CSplitterWnd`物件。

##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn

從分隔器視窗刪除一個資料行。

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>參數

*colDelete*<br/>
指定要刪除的資料行。

### <a name="remarks"></a>備註

此成員函式是由實作 （亦即，如果分隔器視窗有 SPLS_DYNAMIC_SPLIT 樣式） 的動態分隔視窗的邏輯架構呼叫。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。

##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow

從分隔器視窗刪除一個資料列。

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>參數

*rowDelete*<br/>
指定要刪除的資料列。

### <a name="remarks"></a>備註

此成員函式是由實作 （亦即，如果分隔器視窗有 SPLS_DYNAMIC_SPLIT 樣式） 的動態分隔視窗的邏輯架構呼叫。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。

##  <a name="deleteview"></a>  CSplitterWnd::DeleteView

從分隔器視窗刪除一個檢視。

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>參數

*資料列*<br/>
指定要刪除檢視的分隔器視窗的資料列。

*資料行*<br/>
指定要刪除檢視的分隔器視窗資料行。

### <a name="remarks"></a>備註

如果刪除作用中的檢視時，[下一步] 檢視會變成作用中。 預設實作會假設檢視就會自動刪除[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)。

此成員函式是由實作 （亦即，如果分隔器視窗有 SPLS_DYNAMIC_SPLIT 樣式） 的動態分隔視窗的邏輯架構呼叫。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。

##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit

執行鍵盤分隔的命令，通常是 「 視窗分割 」。

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式是高層級的命令，以供[CView](../../mfc/reference/cview-class.md)類別來委派給`CSplitterWnd`實作。

##  <a name="doscroll"></a>  CSplitterWnd::DoScroll

執行同步的分隔視窗捲動。

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*pViewFrom*<br/>
捲動訊息的來源檢視的指標。

*nScrollCode*<br/>
捲軸的程式碼，指出使用者的捲動要求。 這個參數由兩個部分組成： 低序位位元組，這會決定捲動發生水平的型別，以及高序位位元組，這會決定捲動發生垂直的類型：

    - SB_BOTTOM 捲動至底部。

    - SB_LINEDOWN 捲動下一行。

    - SB_LINEUP 捲動上一行。

    - 向下 SB_PAGEDOWN 捲動一頁。

    - 向上 SB_PAGEUP 捲動一頁。

    - SB_TOP 捲動至頂端。

*bDoScroll*<br/>
判斷是否發生指定的捲動動作。 如果*bDoScroll*為 TRUE （也就是子視窗存在，而且如果分隔視窗具有捲軸範圍），則指定的捲動動作可以進行; 如果*bDoScroll*為 FALSE （亦即，如果沒有任何子視窗已存在，或沒有捲軸範圍的分割檢視)，然後捲動不會發生。

### <a name="return-value"></a>傳回值

捲動已同步處理發生時，非零值。否則為 0。

### <a name="remarks"></a>備註

此成員函式是由執行同步的捲動分隔視窗檢視接收捲動訊息時架構呼叫。 覆寫以允許捲動的同步處理之前，需要使用者動作。

##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy

捲動分隔視窗的指定像素數目。

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*pViewFrom*<br/>
捲動訊息的來源檢視的指標。

*sizeScroll*<br/>
水平和垂直捲動的像素數目。

*bDoScroll*<br/>
判斷是否發生指定的捲動動作。 如果*bDoScroll*為 TRUE （也就是子視窗存在，而且如果分隔視窗具有捲軸範圍），則指定的捲動動作可以進行; 如果*bDoScroll*為 FALSE （亦即，如果沒有任何子視窗已存在，或沒有捲軸範圍的分割檢視)，然後捲動不會發生。

### <a name="return-value"></a>傳回值

捲動已同步處理發生時，非零值。否則為 0。

### <a name="remarks"></a>備註

捲動訊息回應中的架構會呼叫此成員函式、 執行同步處理的數量，像素為單位，以捲動分隔視窗*sizeScroll*。 正值表示捲動到右邊;負數的值，表示向上及向左捲動。

需要使用者動作，然後才允許捲動的覆寫。

##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane

判斷焦點或框架中的現用檢視表從 [作用中] 窗格。

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>參數

*pRow*<br/>
指標**int**擷取作用中 窗格的資料列數目。

*pCol*<br/>
指標**int**擷取作用中 窗格的資料行數目。

### <a name="return-value"></a>傳回值

[作用中] 窗格的指標。 如果沒有使用中 窗格則為 NULL。

### <a name="remarks"></a>備註

若要判斷在分隔器視窗中的 [作用中] 窗格，架構被呼叫此成員函式。 覆寫，以要求使用者執行動作才能取得使用中 窗格。

##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount

傳回目前的窗格中的資料行計數。

```
int GetColumnCount() const;
```

### <a name="return-value"></a>傳回值

在分隔器會傳回目前的資料行數目。 靜態分隔器，這也會是資料行數目上限。

##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo

傳回指定的資料行的相關資訊。

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>參數

*資料行*<br/>
指定資料行。

*cxCur*<br/>
參考**int**設為目前的資料行寬度。

*cxMin*<br/>
參考**int**設為目前的最小寬度的資料行。

##  <a name="getpane"></a>  CSplitterWnd::GetPane

傳回在指定的資料列和資料行的窗格。

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>參數

*資料列*<br/>
指定資料列。

*資料行*<br/>
指定資料行。

### <a name="return-value"></a>傳回值

傳回在指定的資料列和資料行的窗格。 傳回的窗格是通常[CView](../../mfc/reference/cview-class.md)-衍生的類別。

##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount

傳回目前的窗格中的資料列計數。

```
int GetRowCount() const;
```

### <a name="return-value"></a>傳回值

在分隔器視窗中，會傳回目前的資料列數目。 靜態分隔視窗中，這也會是資料列數目上限。

##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo

傳回指定的資料列的相關資訊。

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>參數

*資料列*<br/>
指定資料列。

*cyCur*<br/>
若要參考**int**設為目前像素為單位的資料列的高度。

*cyMin*<br/>
若要參考**int**設為目前的最小高度，單位為像素的資料列。

### <a name="remarks"></a>備註

呼叫此成員函式可取得指定的資料列的相關資訊。 *CyCur*參數會填入指定的資料列的目前高度並*cyMin*填滿資料列的最小高度。

##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle

傳回針對分隔器視窗共用的捲軸樣式。

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>傳回值

一或多個下列的 windows 樣式旗標，如果成功：

    - WS_HSCROLL 如果分隔器目前管理共用水平捲軸。

    - WS_VSCROLL 如果分隔器目前管理共用的垂直捲軸。

如果是零，分隔器視窗目前沒有管理任何共用的捲軸。

##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol

取得子視窗窗格中，在指定的資料列和資料行的識別碼。

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>參數

*資料列*<br/>
指定分隔器視窗資料列。

*資料行*<br/>
指定分隔器視窗資料行。

### <a name="return-value"></a>傳回值

窗格的子視窗識別碼。

### <a name="remarks"></a>備註

此成員函式用來建立 nonviews 的窗格，而且可能窗格存在之前呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane

決定是否*pWnd*目前為此分隔視窗的子窗格。

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指標[CWnd](../../mfc/reference/cwnd-class.md)要測試的物件。

*pRow*<br/>
指標**int**用來儲存資料列數目。

*pCol*<br/>
指標**int**用來儲存資料行編號。

### <a name="return-value"></a>傳回值

如果是非零值， *pWnd*是目前子窗格的分隔器視窗中，並*pRow*並*pCol*窗格的位置，在分隔器視窗中會填入。 如果*pWnd*不是子窗格的分隔器視窗中，就會傳回 0。

### <a name="remarks"></a>備註

在 Visual c + + 6.0 之前的版本，此函式定義為

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

這個版本現在已過時，並且不應使用。

##  <a name="istracking"></a>  CSplitterWnd::IsTracking

呼叫以判斷目前正在移動視窗中的分隔器列是否此成員函式。

```
BOOL IsTracking();
```

### <a name="return-value"></a>傳回值

如果分隔器作業正在進行則為非零否則為 0。

##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter

呈現分隔視窗的影像。

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
若要在其中繪製的裝置內容指標。 如果*pDC*是 NULL，則[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)稱為架構並沒有分割繪製視窗。

*n*<br/>
值為`enum ESplitType`，它可以是下列其中一項：

    - `splitBox` 分隔器拖曳方塊中。

    - `splitBar` 出現兩個分割視窗之間的列。

    - `splitIntersection` 分隔視窗的交集。 在 Windows 95/98 上執行時，將不會呼叫這個項目。

    - `splitBorder` 分割視窗框線。

*rect*<br/>
參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定的大小和形狀的分隔視窗。

### <a name="remarks"></a>備註

繪製，並指定確切的分隔器視窗特性，架構會呼叫此成員函式。 覆寫`OnDrawSplitter`進階自訂圖像的分隔器視窗的各種圖形化元件。 預設影像是類似於在 Windows 或 Microsoft Windows 95、windows 98/Microsoft Works 分隔器分隔器列的交集混合在一起。

如需動態分隔視窗的詳細資訊，請參閱 」 分隔器 Windows 」 一文中[多個文件類型、 檢視和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`類別概觀。

##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker

呈現分隔視窗是相同的大小和形狀與框架視窗的影像。

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>參數

*rect*<br/>
若要參考`CRect`物件，指定追蹤的矩形。

### <a name="remarks"></a>備註

此成員函式是由架構呼叫期間的分隔器調整大小。 覆寫`OnInvertTracker`進階自訂分隔器視窗的影像。 預設影像是類似於在 Windows 或 Microsoft Windows 95、windows 98/Microsoft Works 分隔器分隔器列的交集混合在一起。

如需動態分隔視窗的詳細資訊，請參閱 」 分隔器 Windows 」 一文中[多個文件類型、 檢視和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`類別概觀。

##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout

若要重新分隔器視窗顯示調整資料列或資料行的大小之後呼叫。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

呼叫此成員函式，正確重新顯示分隔器視窗之後您已調整資料列和資料行的大小，與, [SetRowInfo](#setrowinfo)並[SetColumnInfo](#setcolumninfo)成員函式。 如果分隔器視窗可見之前，您可以變更為在建立程序的一部分的資料列和資料行的大小，它不需要呼叫此成員函式。

每當使用者分隔器視窗調整大小時，或移動分割時，架構會呼叫此成員函式。

### <a name="example"></a>範例

  範例，請參閱[CSplitterWnd::SetColumnInfo](#setcolumninfo)。

##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane

將框架中作用中的一個窗格的設定。

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>參數

*資料列*<br/>
如果*pWnd*為 NULL 時，會是作用中 窗格中指定的資料列。

*資料行*<br/>
如果*pWnd*為 NULL 時，會是作用中 窗格中指定的資料行。

*pWnd*<br/>
`CWnd` 物件的指標。 如果是 NULL，的窗格中所指定*資料列*並*col*設定作用中。 如果不是 NULL，指定已設定使用中 窗格。

### <a name="remarks"></a>備註

若要設定為使用中的窗格中，當使用者將焦點變更以框架視窗內的窗格，架構被呼叫此成員函式。 您可以明確呼叫`SetActivePane`若要將焦點變更至指定的檢視。

藉由提供資料列和資料行中，指定窗格**或是**藉由提供*pWnd*。

##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo

呼叫以設定指定的資料行資訊。

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>參數

*資料行*<br/>
指定分隔器視窗資料行。

*cxIdeal*<br/>
指定單位為像素的分隔器視窗資料行的理想寬度。

*cxMin*<br/>
指定單位為像素的分隔器視窗資料行的最小寬度。

### <a name="remarks"></a>備註

呼叫此成員函式來設定新的最小寬度與理想寬度資料行。 資料行的最小值會決定何時資料行應該太小而無法完整顯示。

時，架構會顯示分隔器視窗，它會配置資料行和資料列，根據其理想的維度，使用從左上角到右下角的分隔器視窗的工作區中的窗格。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo

呼叫來設定指定的資料列的資訊。

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>參數

*資料列*<br/>
指定分隔器視窗資料列。

*cyIdeal*<br/>
指定的分隔器視窗資料列的理想高度，單位為像素。

*cyMin*<br/>
指定的分隔器視窗資料列的最小高度，單位為像素。

### <a name="remarks"></a>備註

呼叫此成員函式，來設定新的最小高度和資料列的理想高度。 資料列的最小值會判斷何時會太小，無法完全顯示資料列。

時，架構會顯示分隔器視窗，它會配置資料行和資料列，根據其理想的維度，使用從左上角到右下角的分隔器視窗的工作區中的窗格。

##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle

指定新的捲軸樣式分隔器視窗共用捲軸的支援。

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
新的捲軸樣式分隔器視窗共用捲軸的支援，它可以是下列值之一：

- WS_HSCROLL 建立/顯示水平共用的捲軸。

- WS_VSCROLL 建立/顯示垂直共用的捲軸。

### <a name="remarks"></a>備註

一旦建立之後的捲軸它都不會終結即使`SetScrollStyle`呼叫沒有該樣式; 相反地隱藏這些捲軸。 這可讓捲軸來保留其狀態，即使它們隱藏。 之後呼叫`SetScrollStyle`就必須呼叫[RecalcLayout](#recalclayout)才會生效的所有變更。

##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn

指示框架視窗垂直分隔的位置為何。

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>參數

*cxBefore*<br/>
位置 （單位為像素，在分割發生之前）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

垂直分隔視窗建立時，會呼叫此成員函式。 `SplitColumn` 指出發生分割的預設位置。

`SplitColumn` 若要實作動態分隔視窗的邏輯 （也就是如果分隔器視窗有 SPLS_DYNAMIC_SPLIT 樣式） 的架構會呼叫。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。

##  <a name="splitrow"></a>  CSplitterWnd::SplitRow

指示框架視窗水平分割的位置。

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>參數

*cyBefore*<br/>
位置 （單位為像素，在分割發生之前）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

建立水平分隔視窗時，會呼叫此成員函式。 `SplitRow` 指出發生分割的預設位置。

`SplitRow` 若要實作動態分隔視窗的邏輯 （也就是如果分隔器視窗有 SPLS_DYNAMIC_SPLIT 樣式） 的架構會呼叫。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。

##  <a name="ondraw"></a>  CSplitterWnd::OnDraw

由架構呼叫以繪製分隔器視窗。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
裝置內容的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[MFC 範例 VIEWEX](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
