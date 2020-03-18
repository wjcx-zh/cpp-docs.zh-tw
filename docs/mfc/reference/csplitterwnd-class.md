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
ms.openlocfilehash: bee6deed3052d6cc923e432e97ad9a7904060cb6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447445"
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
|[CSplitterWnd：： CSplitterWnd](#csplitterwnd)|呼叫來建立 `CSplitterWnd` 物件的結構。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSplitterWnd：： ActivateNext](#activatenext)|執行下一個窗格或上一個窗格命令。|
|[CSplitterWnd：： CanActivateNext](#canactivatenext)|檢查下一個窗格或上一個窗格命令目前是否可行。|
|[CSplitterWnd：： Create](#create)|呼叫以建立動態分隔視窗，並將它附加至 `CSplitterWnd` 物件。|
|[CSplitterWnd：： CreateScrollBarCtrl](#createscrollbarctrl)|建立共用的捲軸控制項。|
|[CSplitterWnd：： CreateStatic](#createstatic)|呼叫以建立靜態分隔視窗，並將它附加至 `CSplitterWnd` 物件。|
|[CSplitterWnd：： CreateView](#createview)|呼叫以在分隔器視窗中建立窗格。|
|[CSplitterWnd：:D eleteColumn](#deletecolumn)|從分隔器視窗刪除資料行。|
|[CSplitterWnd：:D eleteRow](#deleterow)|從分隔器視窗中刪除資料列。|
|[CSplitterWnd：:D eleteView](#deleteview)|從分隔器視窗刪除視圖。|
|[CSplitterWnd：:D oKeyboardSplit](#dokeyboardsplit)|執行鍵盤分割命令，通常是「視窗分割」。|
|[CSplitterWnd：:D oScroll](#doscroll)|執行分割視窗的同步處理滾動。|
|[CSplitterWnd：:D oScrollBy](#doscrollby)|依指定的圖元數來滾動分割視窗。|
|[CSplitterWnd：： GetActivePane](#getactivepane)|從框架中的焦點或使用中的視圖判斷現用窗格。|
|[CSplitterWnd：： GetColumnCount](#getcolumncount)|傳回目前的窗格資料行計數。|
|[CSplitterWnd：： GetColumnInfo](#getcolumninfo)|傳回指定之資料行的資訊。|
|[CSplitterWnd：： GetPane](#getpane)|傳回位於指定資料列和資料行的窗格。|
|[CSplitterWnd：： GetRowCount](#getrowcount)|傳回目前的窗格資料列計數。|
|[CSplitterWnd：： GetRowInfo](#getrowinfo)|傳回指定之資料列的資訊。|
|[CSplitterWnd：： GetScrollStyle](#getscrollstyle)|傳回共用的捲軸樣式。|
|[CSplitterWnd：： IdFromRowCol](#idfromrowcol)|傳回位於指定資料列和資料行之窗格的子視窗識別碼。|
|[CSplitterWnd：： IsChildPane](#ischildpane)|呼叫以判斷視窗目前是否為此分隔視窗的子窗格。|
|[CSplitterWnd：： IsTracking](#istracking)|判斷是否正在移動分隔器列。|
|[CSplitterWnd：： RecalcLayout](#recalclayout)|呼叫以在調整資料列或資料行大小之後重新顯示分隔視窗。|
|[CSplitterWnd：： SetActivePane](#setactivepane)|將窗格設定為框架中的現用。|
|[CSplitterWnd：： SetColumnInfo](#setcolumninfo)|呼叫以設定指定的資料行資訊。|
|[CSplitterWnd：： SetRowInfo](#setrowinfo)|呼叫以設定指定的資料列資訊。|
|[CSplitterWnd：： SetScrollStyle](#setscrollstyle)|為分隔器視窗的共用捲軸支援指定新的捲軸樣式。|
|[CSplitterWnd：： SplitColumn](#splitcolumn)|指示框架視窗垂直分割的位置。|
|[CSplitterWnd：： SplitRow](#splitrow)|表示框架視窗水準分割的位置。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[CSplitterWnd：： OnDraw](#ondraw)|由架構呼叫以繪製分隔器視窗。|
|[CSplitterWnd：： OnDrawSplitter](#ondrawsplitter)|呈現分割視窗的影像。|
|[CSplitterWnd：： OnInvertTracker](#oninverttracker)|呈現分割視窗的影像，使其與框架視窗具有相同的大小和形狀。|

## <a name="remarks"></a>備註

窗格通常是衍生自[CView](../../mfc/reference/cview-class.md)的應用程式特定物件，但它可以是任何具有適當子視窗識別碼的[CWnd](../../mfc/reference/cwnd-class.md)物件。

`CSplitterWnd` 物件通常內嵌于父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件中。 使用下列步驟建立 `CSplitterWnd` 物件：

1. 在父框架中內嵌 `CSplitterWnd` 成員變數。

2. 覆寫父框架的[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。

3. 從覆寫的 `OnCreateClient`中，呼叫 `CSplitterWnd`的[Create](#create)或[CreateStatic](#createstatic)成員函式。

呼叫 `Create` 成員函式來建立動態分隔器視窗。 動態分隔器視窗通常用來建立和滾動多個相同檔的個別窗格或 views。 架構會自動建立分隔器的初始窗格;然後，當使用者操作分隔視窗的控制項時，架構會建立、調整大小及處置其他窗格。

當您呼叫 `Create`時，您可以指定最小的資料列高度和資料行寬度，以判斷窗格何時太小而無法完整顯示。 呼叫 `Create`之後，您可以藉由呼叫[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函式來調整這些最低限制。

也請使用 `SetColumnInfo` 和 `SetRowInfo` 成員函式來設定資料行的「理想」寬度和資料列的「理想」高度。 當架構顯示分隔視窗時，它會先顯示父框架，然後是分隔視窗。 然後，此架構會根據其理想的維度，在資料行和資料列中配置窗格，從左上到分隔視窗工作區的右下角工作。

動態分隔器視窗中的所有窗格都必須屬於相同的類別。 熟悉的應用程式支援動態分隔視窗，包括 Microsoft Word 和 Microsoft Excel。

使用 `CreateStatic` 成員函式來建立靜態分隔視窗。 使用者只能變更靜態分隔器視窗中的窗格大小，而不是其數目或順序。

當您建立靜態分隔器時，必須特別建立所有靜態分隔器的窗格。 請確定您在父框架的 `OnCreateClient` 成員函式傳回之前建立了所有窗格，否則架構將不會正確顯示視窗。

`CreateStatic` 成員函式會自動將最小資料列高度和資料行寬度為0的靜態分割器初始化。 在您呼叫 `Create`之後，請呼叫[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函式來調整這些最低限制。 您也可以在呼叫 `CreateStatic` 以指出所需的理想窗格維度之後，使用 `SetColumnInfo` 和 `SetRowInfo`。

靜態分隔器的個別窗格通常屬於不同的類別。 如需靜態分隔器視窗的範例，請參閱圖形編輯器和 Windows 檔案管理員。

分隔視窗支援特殊捲軸（除了窗格可能擁有的捲軸外）。 這些捲軸是 `CSplitterWnd` 物件的子系，而且會與窗格共用。

當您建立分隔器視窗時，會建立這些特殊的捲軸。 例如，具有一個資料列、兩個數據行和 WS_VSCROLL 樣式的 `CSplitterWnd` 將會顯示兩個窗格所共用的垂直捲動條。 當使用者移動捲軸時，WM_VSCROLL 的訊息會傳送至兩個窗格。 當窗格設定捲軸位置時，就會設定共用捲軸。

如需分隔視窗的進一步資訊，請參閱[技術提示 29](../../mfc/tn029-splitter-windows.md)。

如需如何建立動態分隔視窗的詳細資訊，請參閱：

- MFC 範例[自由曲線](../../overview/visual-cpp-samples.md)

- MFC 範例[VIEWEX](../../overview/visual-cpp-samples.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>需求

**標頭：** afxext.h。h

##  <a name="activatenext"></a>CSplitterWnd：： ActivateNext

由架構呼叫以執行下一個窗格或上一個窗格命令。

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>參數

*bPrev*<br/>
指出要啟動的視窗。 若為上一個，則為**TRUE** ;[下一步] 為**FALSE** 。

### <a name="remarks"></a>備註

此成員函式是一個高階命令，可供[CView](../../mfc/reference/cview-class.md)類別用來委派給 `CSplitterWnd` 的執行。

##  <a name="canactivatenext"></a>CSplitterWnd：： CanActivateNext

由架構呼叫，以查看下一個窗格或上一個窗格命令目前是否可行。

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>參數

*bPrev*<br/>
指出要啟動的視窗。 若為上一個，則為**TRUE** ;[下一步] 為**FALSE** 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式是一個高階命令，可供[CView](../../mfc/reference/cview-class.md)類別用來委派給 `CSplitterWnd` 的執行。

##  <a name="create"></a>CSplitterWnd：： Create

若要建立動態分隔器視窗，請呼叫 `Create` 成員函式。

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
分隔器視窗的父框架視窗。

*nMaxRows*<br/>
分隔器視窗中的最大資料列數目。 此值不得超過2。

*nMaxCols*<br/>
分隔器視窗中的最大資料行數目。 此值不得超過2。

*sizeMin*<br/>
指定可顯示窗格的大小下限。

*pContext*<br/>
[CCreateCoNtext](../../mfc/reference/ccreatecontext-structure.md)結構的指標。 在大部分的情況下，這可以是傳遞至父框架視窗的*pCoNtext* 。

*dwStyle*<br/>
指定視窗樣式。

*nID*<br/>
視窗的子視窗識別碼。 除非分隔器視窗是嵌套在另一個分隔視窗內，否則識別碼可以 AFX_IDW_PANE_FIRST。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以採取下列步驟，在父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件中內嵌 `CSplitterWnd`：

1. 在父框架中內嵌 `CSplitterWnd` 成員變數。

1. 覆寫父框架的[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。

1. 從覆寫的 `OnCreateClient`內呼叫 `Create` 成員函式。

當您從父框架內建立分隔器視窗時，請將父框架的*pCoNtext*參數傳遞至分隔器視窗。 否則，這個參數可以是 Null。

動態分隔器視窗的初始最小資料列高度和資料行寬度，是由*sizeMin*參數所設定。 這些最小的決定窗格是否太小而無法完整顯示，可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式進行變更。

如需動態分隔器視窗的詳細資訊，請參閱[多個檔案類型、視圖和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技術提示 29](../../mfc/tn029-splitter-windows.md)和 `CSplitterWnd` 類別總覽一文中的「分隔視窗」。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>CSplitterWnd：： CreateScrollBarCtrl

由架構呼叫以建立共用的捲軸控制項。

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定視窗樣式。

*nID*<br/>
視窗的子視窗識別碼。 除非分隔器視窗是嵌套在另一個分隔視窗內，否則識別碼可以 AFX_IDW_PANE_FIRST。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

覆寫 `CreateScrollBarCtrl` 以在捲軸旁包含額外的控制項。 預設行為是建立一般的 Windows 捲軸控制項。

##  <a name="createstatic"></a>CSplitterWnd：： CreateStatic

若要建立靜態分隔視窗，請呼叫 `CreateStatic` 成員函式。

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
分隔器視窗的父框架視窗。

*nRows*<br/>
資料列數目。 這個值不能超過16個。

*nCols*<br/>
資料行數目。 這個值不能超過16個。

*dwStyle*<br/>
指定視窗樣式。

*nID*<br/>
視窗的子視窗識別碼。 除非分隔器視窗是嵌套在另一個分隔視窗內，否則識別碼可以 AFX_IDW_PANE_FIRST。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`CSplitterWnd` 通常會藉由採取下列步驟，內嵌在父 `CFrameWnd` 或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件中：

1. 在父框架中內嵌 `CSplitterWnd` 成員變數。

1. 覆寫父框架的 `OnCreateClient` 成員函式。

1. 從覆寫的[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)內呼叫 `CreateStatic` 成員函式。

靜態分隔視窗包含固定數目的窗格，通常來自不同的類別。

當您建立靜態分隔視窗時，您必須同時建立其所有窗格。 [CreateView](#createview)成員函式通常用於此用途，但您也可以建立其他 nonview 類別。

靜態分隔器視窗的初始最小資料列高度和資料行寬度為0。 這些最小的限制是，可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式來變更窗格何時太小而無法完整顯示。

若要將捲軸加入至靜態分隔視窗，請將 WS_HSCROLL 和 WS_VSCROLL 樣式加入至*dwStyle*。

如需靜態分隔器視窗的詳細資訊，請參閱[多個檔案類型、視圖和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技術提示 29](../../mfc/tn029-splitter-windows.md)和 `CSplitterWnd` 類別總覽一文中的「分隔視窗」。

##  <a name="createview"></a>CSplitterWnd：： CreateView

建立靜態分隔器視窗的窗格。

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

*row*<br/>
指定要在其中放置新視圖的分隔器視窗資料列。

*col*<br/>
指定要在其中放置新視圖的分隔器視窗資料行。

*pViewClass*<br/>
指定新視圖的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 。

*sizeInit*<br/>
指定新視圖的初始大小。

*pContext*<br/>
用來建立視圖的建立內容指標（通常是傳遞至父框架的已覆寫[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式的*pCoNtext* ，在其中建立分隔器視窗）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您必須先建立靜態分隔器視窗的所有窗格，架構才會顯示分隔器。

當動態分隔器視窗的使用者分割窗格、資料列或資料行時，架構也會呼叫這個成員函式來建立新的窗格。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>CSplitterWnd：： CSplitterWnd

呼叫來建立 `CSplitterWnd` 物件的結構。

```
CSplitterWnd();
```

### <a name="remarks"></a>備註

以兩個步驟來建立 `CSplitterWnd` 物件。 首先，呼叫會建立 `CSplitterWnd` 物件的函式，然後呼叫[Create](#create)成員函式，該函式會建立分隔器視窗，並將它附加至 `CSplitterWnd` 物件。

##  <a name="deletecolumn"></a>CSplitterWnd：:D eleteColumn

從分隔器視窗刪除資料行。

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>參數

*colDelete*<br/>
指定要刪除的資料行。

### <a name="remarks"></a>備註

此成員函式會由架構呼叫，以執行動態分隔器視窗的邏輯（也就是，如果分隔視窗具有 SPLS_DYNAMIC_SPLIT 樣式）。 它可以自訂，以及虛擬函式[CreateView](#createview)，以執行更先進的動態分隔器。

##  <a name="deleterow"></a>CSplitterWnd：:D eleteRow

從分隔器視窗中刪除資料列。

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>參數

*rowDelete*<br/>
指定要刪除的資料列。

### <a name="remarks"></a>備註

此成員函式會由架構呼叫，以執行動態分隔器視窗的邏輯（也就是，如果分隔視窗具有 SPLS_DYNAMIC_SPLIT 樣式）。 它可以自訂，以及虛擬函式[CreateView](#createview)，以執行更先進的動態分隔器。

##  <a name="deleteview"></a>CSplitterWnd：:D eleteView

從分隔器視窗刪除視圖。

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>參數

*row*<br/>
指定要刪除其視圖的分隔器視窗資料列。

*col*<br/>
指定要刪除其視圖的分隔器視窗資料行。

### <a name="remarks"></a>備註

如果正在刪除即時檢視，下一個視圖將會變成作用中。 預設的執行會假設此視圖會在[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)中自動刪除。

此成員函式會由架構呼叫，以執行動態分隔器視窗的邏輯（也就是，如果分隔視窗具有 SPLS_DYNAMIC_SPLIT 樣式）。 它可以自訂，以及虛擬函式[CreateView](#createview)，以執行更先進的動態分隔器。

##  <a name="dokeyboardsplit"></a>CSplitterWnd：:D oKeyboardSplit

執行鍵盤分割命令，通常是「視窗分割」。

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式是一個高階命令，可供[CView](../../mfc/reference/cview-class.md)類別用來委派給 `CSplitterWnd` 的執行。

##  <a name="doscroll"></a>CSplitterWnd：:D oScroll

執行分割視窗的同步處理滾動。

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*pViewFrom*<br/>
要從中產生捲軸訊息之視圖的指標。

*nScrollCode*<br/>
表示使用者的滾動要求的捲軸程式碼。 這個參數是由兩個部分組成：低序位位元組，可決定水準發生的滾動類型，而高序位位元組則會決定垂直發生的滾動類型：

- SB_BOTTOM 向下滾動。

- SB_LINEDOWN 向下滾動一行。

- SB_LINEUP 向上滾動一行。

- SB_PAGEDOWN 向下滾動一頁。

- SB_PAGEUP 向上滾動一頁。

- SB_TOP 滾動到頁首。

*bDoScroll*<br/>
判斷是否發生指定的滾動動作。 如果*bDoScroll*為 TRUE （亦即，如果子視窗存在，而且分割視窗具有捲軸範圍），則會進行指定的滾動動作。如果*bDoScroll*為 FALSE （亦即，如果沒有子視窗存在，或分割視圖沒有捲軸範圍），則不會進行滾動。

### <a name="return-value"></a>傳回值

如果發生同步處理的滾動則為非零值;否則為0。

### <a name="remarks"></a>備註

此成員函式會由架構呼叫，以便在視圖收到捲軸訊息時，執行已同步處理的分割視窗滾動。 在允許同步處理的滾動之前，覆寫以要求使用者採取動作。

##  <a name="doscrollby"></a>CSplitterWnd：:D oScrollBy

依指定的圖元數來滾動分割視窗。

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*pViewFrom*<br/>
要從中產生捲軸訊息之視圖的指標。

*sizeScroll*<br/>
水準和垂直捲動的圖元數。

*bDoScroll*<br/>
判斷是否發生指定的滾動動作。 如果*bDoScroll*為 TRUE （亦即，如果子視窗存在，而且分割視窗具有捲軸範圍），則會進行指定的滾動動作。如果*bDoScroll*為 FALSE （亦即，如果沒有子視窗存在，或分割視圖沒有捲軸範圍），則不會進行滾動。

### <a name="return-value"></a>傳回值

如果發生同步處理的滾動則為非零值;否則為0。

### <a name="remarks"></a>備註

架構會呼叫這個成員函式來回應捲軸訊息，以根據*sizeScroll*所表示的量（以圖元為單位）來執行分割視窗的同步滾動。 正數值表示向下和向右滾動;負數值表示向上和向左滾動。

在允許 scroll 之前，覆寫以要求使用者採取動作。

##  <a name="getactivepane"></a>CSplitterWnd：： GetActivePane

從框架中的焦點或使用中的視圖判斷現用窗格。

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>參數

*pRow*<br/>
**Int**的指標，用來抓取現用窗格的資料列編號。

*pCol*<br/>
**Int**的指標，用來抓取現用窗格的資料行編號。

### <a name="return-value"></a>傳回值

現用窗格的指標。 如果沒有作用中窗格存在，則為 Null。

### <a name="remarks"></a>備註

此成員函式是由架構呼叫，以判斷分隔器視窗中的使用中窗格。 在取得使用中窗格之前，覆寫以要求使用者採取動作。

##  <a name="getcolumncount"></a>CSplitterWnd：： GetColumnCount

傳回目前的窗格資料行計數。

```
int GetColumnCount() const;
```

### <a name="return-value"></a>傳回值

傳回分割器中目前的資料行數目。 若為靜態分隔器，這也會是資料行的最大數目。

##  <a name="getcolumninfo"></a>CSplitterWnd：： GetColumnInfo

傳回指定之資料行的資訊。

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>參數

*col*<br/>
指定資料行。

*cxCur*<br/>
要設定為目前資料行寬度之**int**的參考。

*cxMin*<br/>
要設定為目前資料行最小寬度之**int**的參考。

##  <a name="getpane"></a>CSplitterWnd：： GetPane

傳回位於指定資料列和資料行的窗格。

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>參數

*row*<br/>
指定資料列。

*col*<br/>
指定資料行。

### <a name="return-value"></a>傳回值

傳回位於指定資料列和資料行的窗格。 傳回的窗格通常是[CView](../../mfc/reference/cview-class.md)衍生的類別。

##  <a name="getrowcount"></a>CSplitterWnd：： GetRowCount

傳回目前的窗格資料列計數。

```
int GetRowCount() const;
```

### <a name="return-value"></a>傳回值

傳回分隔器視窗中目前的資料列數目。 若為靜態分隔視窗，這也會是資料列的最大數目。

##  <a name="getrowinfo"></a>CSplitterWnd：： GetRowInfo

傳回指定之資料列的資訊。

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>參數

*row*<br/>
指定資料列。

*cyCur*<br/>
要設定為目前資料列高度（以圖元為單位）的**int**參考。

*cyMin*<br/>
要設定為數據列目前最小高度的**int**參考（以圖元為單位）。

### <a name="remarks"></a>備註

呼叫這個成員函式，以取得指定資料列的相關資訊。 *CyCur*參數會填入指定資料列的目前高度，而*cyMin*則會填入資料列的最小高度。

##  <a name="getscrollstyle"></a>CSplitterWnd：： GetScrollStyle

傳回分隔器視窗的共用捲軸樣式。

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>傳回值

下列一或多個 windows 樣式旗標（如果成功）：

- 如果分割器目前管理共用水準捲軸，WS_HSCROLL。

- 如果分割器目前管理共用的垂直捲動條，則 WS_VSCROLL。

如果為零，則分隔器視窗目前不會管理任何共用的捲軸。

##  <a name="idfromrowcol"></a>CSplitterWnd：： IdFromRowCol

取得位於指定資料列和資料行之窗格的子視窗識別碼。

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>參數

*row*<br/>
指定分隔器視窗的資料列。

*col*<br/>
指定分隔器視窗資料行。

### <a name="return-value"></a>傳回值

窗格的子視窗識別碼。

### <a name="remarks"></a>備註

這個成員函式是用來建立 nonviews 作為窗格，而且可以在窗格存在之前呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>CSplitterWnd：： IsChildPane

判斷*pWnd*目前是否為此分隔視窗的子窗格。

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
要測試之[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

*pRow*<br/>
要儲存資料列編號之**int**的指標。

*pCol*<br/>
要儲存資料行編號之**int**的指標。

### <a name="return-value"></a>傳回值

如果是非零值， *pWnd*目前是此分隔器視窗的子窗格，而*pRow*和*pCol*會填入窗格在分隔視窗中的位置。 如果*pWnd*不是此分隔器視窗的子窗格，則會傳回0。

### <a name="remarks"></a>備註

在 6.0 C++之前的 Visual 版本中，此函式定義為

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

此版本現在已過時，不應使用。

##  <a name="istracking"></a>CSplitterWnd：： IsTracking

呼叫這個成員函式，以判斷視窗中的分隔器列是否正在移動中。

```
BOOL IsTracking();
```

### <a name="return-value"></a>傳回值

如果分隔器作業正在進行中，則為非零;否則為0。

##  <a name="ondrawsplitter"></a>CSplitterWnd：： OnDrawSplitter

呈現分割視窗的影像。

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要在其中繪製之裝置內容的指標。 如果*pDC*是 Null，則會由架構呼叫[CWnd：： RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) ，而且不會繪製任何分割視窗。

*nType*<br/>
`enum ESplitType`的值，它可以是下列其中一項：

- `splitBox` [分隔器] 拖曳框。

- `splitBar` 出現在兩個分割視窗之間的橫條。

- `splitIntersection` 分割視窗的交集。 在 Windows 95/98 上執行時，將不會呼叫此元素。

- `splitBorder` 分割視窗框線。

*各種*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的參考，指定分割視窗的大小和形狀。

### <a name="remarks"></a>備註

此成員函式會由架構呼叫，以繪製和指定分隔器視窗的確切特性。 針對分隔器視窗的各種圖形元件，覆寫影像自訂的 `OnDrawSplitter`。 預設影像類似于 Microsoft 適用于 Windows 或 Microsoft Windows 95/98 的分隔線，因為分隔器列的交集會混合在一起。

如需動態分隔器視窗的詳細資訊，請參閱[多個檔案類型、視圖和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技術提示 29](../../mfc/tn029-splitter-windows.md)和 `CSplitterWnd` 類別總覽一文中的「分隔視窗」。

##  <a name="oninverttracker"></a>CSplitterWnd：： OnInvertTracker

呈現分割視窗的影像，使其與框架視窗具有相同的大小和形狀。

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>參數

*各種*<br/>
指定追蹤矩形之 `CRect` 物件的參考。

### <a name="remarks"></a>備註

此成員函式會在調整分隔器的大小時由架構呼叫。 覆寫分隔器視窗影像之自訂的 `OnInvertTracker`。 預設影像類似于 Microsoft 適用于 Windows 或 Microsoft Windows 95/98 的分隔線，因為分隔器列的交集會混合在一起。

如需動態分隔器視窗的詳細資訊，請參閱[多個檔案類型、視圖和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技術提示 29](../../mfc/tn029-splitter-windows.md)和 `CSplitterWnd` 類別總覽一文中的「分隔視窗」。

##  <a name="recalclayout"></a>CSplitterWnd：： RecalcLayout

呼叫以在調整資料列或資料行大小之後重新顯示分隔視窗。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>備註

當您使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式來調整資料列和資料行的大小時，請呼叫此成員函式以正確重新顯示分隔視窗。 如果您在建立程式的過程中變更資料列和資料行的大小，以顯示分隔視窗，則不需要呼叫這個成員函式。

每當使用者調整分隔器視窗的大小或移動分割時，架構就會呼叫這個成員函式。

### <a name="example"></a>範例

  請參閱[CSplitterWnd：： SetColumnInfo](#setcolumninfo)的範例。

##  <a name="setactivepane"></a>CSplitterWnd：： SetActivePane

將窗格設定為框架中的現用。

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>參數

*row*<br/>
如果*pWnd*為 Null，則會在窗格中指定將使用的資料列。

*col*<br/>
如果*pWnd*為 Null，則會在窗格中指定將使用的資料行。

*pWnd*<br/>
`CWnd` 物件的指標。 如果是 Null，*則會將*資料列和資料*行*所指定的窗格設定為使用中。 如果不是 Null，則指定設定為作用中的窗格。

### <a name="remarks"></a>備註

當使用者將焦點變更為框架視窗內的窗格時，架構會呼叫這個成員函式將窗格設定為作用中。 您可以明確地呼叫 `SetActivePane`，將焦點變更為指定的 view。

指定 [窗格]，方法是提供資料列和資料行，**或**提供*pWnd*。

##  <a name="setcolumninfo"></a>CSplitterWnd：： SetColumnInfo

呼叫以設定指定的資料行資訊。

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>參數

*col*<br/>
指定分隔器視窗資料行。

*cxIdeal*<br/>
指定分隔器視窗資料行的理想寬度（以圖元為單位）。

*cxMin*<br/>
指定分隔器視窗資料行的最小寬度（以圖元為單位）。

### <a name="remarks"></a>備註

呼叫這個成員函式，為數據行設定新的最小寬度和理想寬度。 [資料行最小值] 會決定資料行太小而無法完整顯示的時間。

當架構顯示分隔器視窗時，它會根據其理想的維度來配置資料行和資料列中的窗格，而從左上角到分隔視窗工作區的右下角工作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>CSplitterWnd：： SetRowInfo

呼叫以設定指定的資料列資訊。

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>參數

*row*<br/>
指定分隔視窗的資料列。

*cyIdeal*<br/>
指定分隔器視窗資料列的理想高度（以圖元為單位）。

*cyMin*<br/>
指定分隔器視窗資料列的最小高度（以圖元為單位）。

### <a name="remarks"></a>備註

呼叫這個成員函式，為數據列設定新的最小高度和理想高度。 [資料列最小值] 會決定資料列太小而無法完整顯示的時間。

當架構顯示分隔器視窗時，它會根據其理想的維度來配置資料行和資料列中的窗格，而從左上角到分隔視窗工作區的右下角工作。

##  <a name="setscrollstyle"></a>CSplitterWnd：： SetScrollStyle

為分隔器視窗的共用捲軸支援指定新的滾動樣式。

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
分隔器視窗的共用捲軸支援的新 scroll 樣式，可以是下列其中一個值：

- WS_HSCROLL 建立/顯示水準共用捲軸。

- WS_VSCROLL 建立/顯示垂直共用捲軸。

### <a name="remarks"></a>備註

建立捲軸之後，即使在沒有該樣式的情況下呼叫 `SetScrollStyle`，也不會損毀。而是隱藏那些捲軸。 這可讓捲軸保留其狀態，即使隱藏起來也一樣。 呼叫 `SetScrollStyle` 之後，必須呼叫[RecalcLayout](#recalclayout) ，所有變更才會生效。

##  <a name="splitcolumn"></a>CSplitterWnd：： SplitColumn

指示框架視窗垂直分割的位置。

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>參數

*cxBefore*<br/>
分割發生之前的位置（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

建立垂直分隔器視窗時，會呼叫這個成員函式。 `SplitColumn` 表示發生分割的預設位置。

`SplitColumn` 由架構呼叫，以執行動態分隔器視窗的邏輯（也就是，如果分隔視窗具有 SPLS_DYNAMIC_SPLIT 樣式）。 它可以自訂，以及虛擬函式[CreateView](#createview)，以執行更先進的動態分隔器。

##  <a name="splitrow"></a>CSplitterWnd：： SplitRow

表示框架視窗水準分割的位置。

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>參數

*cyBefore*<br/>
分割發生之前的位置（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

建立水準分隔器視窗時，會呼叫這個成員函式。 `SplitRow` 表示發生分割的預設位置。

`SplitRow` 由架構呼叫，以執行動態分隔器視窗的邏輯（也就是，如果分隔視窗具有 SPLS_DYNAMIC_SPLIT 樣式）。 它可以自訂，以及虛擬函式[CreateView](#createview)，以執行更先進的動態分隔器。

##  <a name="ondraw"></a>CSplitterWnd：： OnDraw

由架構呼叫以繪製分隔器視窗。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
裝置內容的指標。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[MFC 範例 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
