---
title: CSplitterWnd 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 071eaeef6fbdbe4967d184936f5fb7bffb7786b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|呼叫建構`CSplitterWnd`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|執行下一個窗格或上一個窗格的命令。|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|檢查如果下一個窗格或上一個窗格命令目前是否可用。|  
|[CSplitterWnd::Create](#create)|若要建立動態分隔視窗，並將其附加至呼叫`CSplitterWnd`物件。|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|建立共用的捲軸控制項。|  
|[CSplitterWnd::CreateStatic](#createstatic)|若要建立靜態分隔視窗，並將其附加至呼叫`CSplitterWnd`物件。|  
|[CSplitterWnd::CreateView](#createview)|呼叫以建立在分隔視窗的窗格。|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|從分隔視窗刪除一個資料行。|  
|[CSplitterWnd::DeleteRow](#deleterow)|從分隔視窗刪除一個資料列。|  
|[CSplitterWnd::DeleteView](#deleteview)|從分隔視窗刪除一個檢視。|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|執行鍵盤分隔的命令，通常是 「 視窗分割 」。|  
|[CSplitterWnd::DoScroll](#doscroll)|執行同步的分隔視窗捲動。|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|捲動分隔視窗，以像素為單位的指定數目。|  
|[CSplitterWnd::GetActivePane](#getactivepane)|決定從焦點或作用中檢視的框架中作用中的窗格。|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|傳回目前的窗格資料行計數。|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|傳回指定之資料行的相關資訊。|  
|[CSplitterWnd::GetPane](#getpane)|傳回在指定的資料列和資料行的窗格。|  
|[CSplitterWnd::GetRowCount](#getrowcount)|傳回目前的窗格中的資料列計數。|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|傳回指定的資料列的相關資訊。|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|傳回共用的捲軸樣式。|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|傳回的子視窗窗格中，在指定的資料列和資料行識別碼。|  
|[CSplitterWnd::IsChildPane](#ischildpane)|呼叫以判斷視窗是否是目前子此分隔視窗窗格。|  
|[CSplitterWnd::IsTracking](#istracking)|判斷目前正在移動分隔列是否。|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|若要重新分隔視窗顯示調整資料列或資料行的大小之後呼叫。|  
|[CSplitterWnd::SetActivePane](#setactivepane)|將框架中作用中的一個窗格的設定。|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|呼叫以設定所指定的資料行資訊。|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|設定所指定的資料列資訊的呼叫。|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|指定新的分隔視窗的捲軸樣式共用捲軸的支援。|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|指示框架視窗垂直分隔的位置為何。|  
|[CSplitterWnd::SplitRow](#splitrow)|指示框架視窗水平分隔的位置為何。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|由架構呼叫以繪製分隔視窗。|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|呈現分隔視窗的映像。|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|呈現分隔視窗是相同大小與外型框架視窗的映像。|  
  
## <a name="remarks"></a>備註  
 窗格是通常衍生自特定應用程式物件[CView](../../mfc/reference/cview-class.md)，但它可以是任何[CWnd](../../mfc/reference/cwnd-class.md)具有適當的子視窗識別碼。  
  
 A`CSplitterWnd`物件通常內嵌在父代[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件。 建立`CSplitterWnd`物件使用下列步驟：  
  
1.  內嵌`CSplitterWnd`父框架中的成員變數。  
  
2.  覆寫父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。  
  
3.  從覆寫`OnCreateClient`，呼叫[建立](#create)或[CreateStatic](#createstatic)成員函式`CSplitterWnd`。  
  
 呼叫**建立**成員函式來建立動態分隔視窗。 動態分隔視窗通常用來建立及捲動多個個別的窗格或檢視相同文件。 架構會自動建立分隔器; 的初始窗格然後架構建立、 調整大小，並處置其他窗格與使用者分隔視窗的控制項。  
  
 當您呼叫**建立**，指定最小資料列高度和資料行寬度，以決定何時窗格太小而無法完整顯示。 在您呼叫後**建立**，您可以調整的最小值，藉由呼叫[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函式。  
  
 也使用`SetColumnInfo`和`SetRowInfo`設定資料行 」 理想 「 寬度 」 和 「"理想"的資料列高度的成員函式。 當 framework 顯示在分隔視窗時，它會先顯示父框架，然後分隔視窗。 架構然後配置中資料行和資料列，根據其理想的維度，使用從左上角到右下角分隔視窗工作區的窗格。  
  
 動態分隔視窗中的所有窗格都必須屬於相同的類別。 熟悉支援動態分隔視窗的應用程式包括 Microsoft Word 和 Microsoft Excel。  
  
 使用`CreateStatic`建立靜態分隔視窗的成員函式。 使用者可以變更靜態分隔視窗，其數目或順序不使用中窗格的大小。  
  
 具體而言，當您建立靜態分隔器，您必須建立所有靜態分隔的窗格。 請確定您建立父框架之前的所有窗格`OnCreateClient`成員函式會傳回，否則架構會無法正確顯示視窗。  
  
 `CreateStatic`成員函式會自動初始化靜態分隔器與最小資料列高度和資料行寬度為 0。 在您呼叫後**建立**，調整的最小值，藉由呼叫[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函式。 也使用`SetColumnInfo`和`SetRowInfo`呼叫之後`CreateStatic`以指出預期理想窗格維度。  
  
 靜態分隔器的個別窗格通常屬於不同類別。 如需靜態分隔視窗的範例，請參閱圖形編輯器和 Windows 檔案管理員。  
  
 分隔視窗支援特殊的捲軸 （除了窗格可能會有捲軸）。 這些捲軸是子系`CSplitterWnd`物件，並與窗格共用。  
  
 當您建立分隔視窗時，您會建立這些特殊的捲軸。 比方說，`CSplitterWnd`具有一個資料列中，兩個資料行，而**WS_VSCROLL**樣式，將顯示垂直捲軸的兩個窗格。 當使用者將捲軸，`WM_VSCROLL`訊息傳送至這兩個窗格。 當窗格設定捲軸位置時，會設定共用的捲軸。  
  
 如需分隔視窗的詳細資訊，請參閱：  
  
- [技術提示 29](../../mfc/tn029-splitter-windows.md)  
  
-   知識庫文章 Q262024： 如何： 使用 CPropertySheet 為 CSplitterWnd 子  
  
 如需有關如何建立動態分隔視窗的詳細資訊，請參閱：  
  
-   MFC 範例[Scribble](../../visual-cpp-samples.md)  
  
-   MFC 範例[VIEWEX](../../visual-cpp-samples.md)。  
  
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
 `bPrev`  
 表示啟用哪一個視窗。 **TRUE**的上一個;**FALSE**的下一步。  
  
### <a name="remarks"></a>備註  
 此成員函式是高層級的命令，以供[CView](../../mfc/reference/cview-class.md)類別，以委派給`CSplitterWnd`實作。  
  
##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext  
 若要檢查的下一個窗格或上一個窗格的命令目前架構呼叫。  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bPrev`  
 表示啟用哪一個視窗。 **TRUE**的上一個;**FALSE**的下一步。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式是高層級的命令，以供[CView](../../mfc/reference/cview-class.md)類別，以委派給`CSplitterWnd`實作。  
  
##  <a name="create"></a>  CSplitterWnd::Create  
 若要建立動態分隔視窗，呼叫**建立**成員函式。  
  
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
 `pParentWnd`  
 分隔視窗的父框架視窗。  
  
 *nMaxRows*  
 分隔視窗中的資料列的數目上限。 此值不能超過 2。  
  
 *nMaxCols*  
 分隔視窗中的資料行的數目上限。 此值不能超過 2。  
  
 `sizeMin`  
 指定的速率可能會顯示一個窗格的大小下限。  
  
 `pContext`  
 指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 在大部分情況下，這可以是`pContext`傳遞給父框架視窗。  
  
 `dwStyle`  
 指定的視窗樣式。  
  
 `nID`  
 視窗的子視窗識別碼。 識別碼可以是**AFX_IDW_PANE_FIRST**除非分隔視窗是否位於另一個分隔視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以將內嵌`CSplitterWnd`父系中[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件採取下列步驟：  
  
1.  內嵌`CSplitterWnd`父框架中的成員變數。  
  
2.  覆寫父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。  
  
3.  呼叫**建立**從覆寫的成員函式`OnCreateClient`。  
  
 當您建立分隔視窗從父系範圍內時，傳遞父框架`pContext`分隔視窗的參數。 否則，這個參數可以是**NULL**。  
  
 動態分隔視窗的初始最小資料列高度和資料行寬度由設定`sizeMin`參數。 這些最小值，判斷是否為太小而無法完整顯示 窗格，可以變更與[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式。  
  
 如需動態分隔視窗的詳細資訊，請參閱 「 分隔視窗 」 文章中[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`類別概觀。  
  
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
 `dwStyle`  
 指定的視窗樣式。  
  
 `nID`  
 視窗的子視窗識別碼。 識別碼可以是**AFX_IDW_PANE_FIRST**除非分隔視窗是否位於另一個分隔視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫`CreateScrollBarCtrl`包含額外的控制項捲軸旁邊。 預設行為是建立標準 Windows 捲軸控制項。  
  
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
 `pParentWnd`  
 分隔視窗的父框架視窗。  
  
 `nRows`  
 列的數目。 此值不能超過 16。  
  
 *nCols*  
 行數。 此值不能超過 16。  
  
 `dwStyle`  
 指定的視窗樣式。  
  
 `nID`  
 視窗的子視窗識別碼。 識別碼可以是**AFX_IDW_PANE_FIRST**除非分隔視窗是否位於另一個分隔視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 A`CSplitterWnd`通常會內嵌在父代`CFrameWnd`或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件採取下列步驟：  
  
1.  內嵌`CSplitterWnd`父框架中的成員變數。  
  
2.  覆寫父框架`OnCreateClient`成員函式。  
  
3.  呼叫`CreateStatic`從覆寫的成員函式[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。  
  
 靜態分隔視窗包含固定的數目的窗格，通常是來自不同類別。  
  
 當您建立靜態分隔視窗時，您必須同時建立其所有窗格。 [CreateView](#createview)成員函式通常用於此目的，但您可以建立其他 nonview 類別。  
  
 靜態分隔視窗的初始最小資料列高度和資料行寬度是 0。 這些最小值，判斷太小而無法完整顯示一個窗格時，可以變更與[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式。  
  
 若要加入至靜態分隔視窗的捲軸，加入**WS_HSCROLL**和**WS_VSCROLL**樣式到`dwStyle`。  
  
 請參閱文件中的 「 分隔視窗 」[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`如需有關靜態分隔視窗類別概觀。  
  
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
 `row`  
 指定要放置新檢視的分隔視窗資料列。  
  
 `col`  
 指定要放置新檢視的分隔視窗資料行。  
  
 `pViewClass`  
 指定[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)新的檢視。  
  
 *sizeInit*  
 指定新的檢視表的初始大小。  
  
 `pContext`  
 建立內容，用來建立檢視的指標 (通常`pContext`傳入父框架覆寫[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)在其中建立分隔視窗的成員函式)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 必須先建立所有靜態分隔視窗的窗格，架構會顯示用來分隔。  
  
 架構也會呼叫此成員函式，建立新的窗格，當使用者動態分隔視窗的分割窗格中，資料列或資料行。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd  
 呼叫建構`CSplitterWnd`物件。  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>備註  
 建構`CSplitterWnd`兩個步驟中的物件。 首先，呼叫建構函式，建立`CSplitterWnd`物件，然後再呼叫[建立](#create)成員函式，以建立分隔視窗，並將它附加至`CSplitterWnd`物件。  
  
##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn  
 從分隔視窗刪除一個資料行。  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>參數  
 *colDelete*  
 指定要刪除的資料行。  
  
### <a name="remarks"></a>備註  
 若要實作動態分隔視窗的邏輯架構會呼叫此成員函式 (亦即，如果分隔視窗具有**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow  
 從分隔視窗刪除一個資料列。  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>參數  
 *rowDelete*  
 指定要刪除的資料列。  
  
### <a name="remarks"></a>備註  
 若要實作動態分隔視窗的邏輯架構會呼叫此成員函式 (亦即，如果分隔視窗具有**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="deleteview"></a>  CSplitterWnd::DeleteView  
 從分隔視窗刪除一個檢視。  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>參數  
 `row`  
 指定要刪除檢視的分隔視窗資料列。  
  
 `col`  
 指定要刪除檢視的分隔視窗資料行。  
  
### <a name="remarks"></a>備註  
 如果刪除使用中的檢視時，會變成作用中下一個檢視。 預設實作會假設檢視就會自動刪除[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)。  
  
 若要實作動態分隔視窗的邏輯架構會呼叫此成員函式 (亦即，如果分隔視窗具有**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit  
 執行鍵盤分隔的命令，通常是 「 視窗分割 」。  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式是高層級的命令，以供[CView](../../mfc/reference/cview-class.md)類別，以委派給`CSplitterWnd`實作。  
  
##  <a name="doscroll"></a>  CSplitterWnd::DoScroll  
 執行同步的分隔視窗捲動。  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pViewFrom`  
 捲動訊息的來源檢視的指標。  
  
 `nScrollCode`  
 捲軸程式碼，表示使用者的捲動要求。 這個參數由兩個部分組成： 低序位位元組，這會決定捲動發生水平的型別，以及高序位位元組，這會決定捲動發生垂直的類型：  
  
- **SB_BOTTOM**往下捲動。  
  
- **SB_LINEDOWN**向下捲動一行。  
  
- **SB_LINEUP**向上捲動一行。  
  
- **SB_PAGEDOWN**向下捲動一頁。  
  
- **SB_PAGEUP**向上捲動一頁。  
  
- **SB_TOP**捲動至頂端。  
  
 `bDoScroll`  
 判斷是否發生指定的捲動動作。 如果`bDoScroll`是**TRUE** （也就是子視窗已存在，而且如果分隔視窗具有捲軸範圍），然後指定捲動動作可以進行; 如果`bDoScroll`是**FALSE** （亦即，如果沒有任何子視窗已存在，或分割檢視有沒有捲軸範圍），然後捲動不會發生。  
  
### <a name="return-value"></a>傳回值  
 如果同步處理則為非零捲動，就會發生。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此成員函式是由執行同步的捲動分隔視窗檢視接收捲動訊息時架構呼叫。 覆寫，以允許捲動的同步處理之前，需要使用者動作。  
  
##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy  
 捲動分隔視窗，以像素為單位的指定數目。  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pViewFrom`  
 捲動訊息的來源檢視的指標。  
  
 `sizeScroll`  
 水平和垂直捲動的像素數目。  
  
 bDoScroll  
 判斷是否發生指定的捲動動作。 如果`bDoScroll`是**TRUE** （也就是子視窗已存在，而且如果分隔視窗具有捲軸範圍），然後指定捲動動作可以進行; 如果`bDoScroll`是**FALSE** （亦即，如果沒有任何子視窗已存在，或分割檢視有沒有捲軸範圍），然後捲動不會發生。  
  
### <a name="return-value"></a>傳回值  
 如果同步處理則為非零捲動，就會發生。否則便是 0。  
  
### <a name="remarks"></a>備註  
 捲動訊息的回應中的架構會呼叫此成員函式、 執行同步處理量，單位為像素所指示的分隔視窗捲動`sizeScroll`。 正值表示捲動往下及往右;負數值表示向上及向左捲動。  
  
 需要使用者動作，才能允許捲動的覆寫。  
  
##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane  
 決定從焦點或作用中檢視的框架中作用中的窗格。  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pRow`  
 指標**int**擷取使用中 窗格中的資料列數目。  
  
 `pCol`  
 指標**int**擷取使用中 窗格中的資料行數目。  
  
### <a name="return-value"></a>傳回值  
 使用中窗格的指標。 **NULL**是否有任何作用中 窗格。  
  
### <a name="remarks"></a>備註  
 若要判斷在分隔視窗中 [作用中的] 窗格的 framework 會呼叫此成員函式。 覆寫，以要求使用者執行動作才能取得使用中 窗格。  
  
##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount  
 傳回目前的窗格資料行計數。  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在分隔器會傳回目前的資料行數目。 靜態分隔器，這也會是資料行數目上限。  
  
##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo  
 傳回指定之資料行的相關資訊。  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>參數  
 `col`  
 指定資料行。  
  
 *cxCur*  
 若要參考`int`設為目前的資料行寬度。  
  
 `cxMin`  
 若要參考`int`設為資料行的目前最小寬度。  
  
##  <a name="getpane"></a>  CSplitterWnd::GetPane  
 傳回在指定的資料列和資料行的窗格。  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>參數  
 `row`  
 指定資料列。  
  
 `col`  
 指定資料行。  
  
### <a name="return-value"></a>傳回值  
 傳回在指定的資料列和資料行的窗格。 傳回的窗格是通常[CView](../../mfc/reference/cview-class.md)-衍生的類別。  
  
##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount  
 傳回目前的窗格中的資料列計數。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 分隔視窗中傳回目前的列數。 靜態分隔視窗中，這也會是資料列數目上限。  
  
##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo  
 傳回指定的資料列的相關資訊。  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>參數  
 `row`  
 指定資料列。  
  
 `cyCur`  
 若要參考`int`設為目前像素為單位的資料列的高度。  
  
 `cyMin`  
 若要參考`int`設為目前的最小高度，單位為像素的資料列。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式可取得指定的資料列的相關資訊。 `cyCur`參數會填入目前指定的資料列的高度和`cyMin`填滿的資料列的最小高度。  
  
##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle  
 傳回分隔視窗的共用的捲軸樣式。  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一或多個下列的視窗樣式旗標，如果成功：  
  
- **WS_HSCROLL**如果分隔器目前管理共用水平捲軸。  
  
- **WS_VSCROLL**如果分隔器目前管理共用的垂直捲軸。  
  
 如果是零，分隔視窗目前沒有管理任何共用的捲軸。  
  
##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol  
 取得子視窗窗格中，在指定的資料列和資料行的識別碼。  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>參數  
 `row`  
 指定分隔視窗資料列。  
  
 `col`  
 指定分隔視窗資料行。  
  
### <a name="return-value"></a>傳回值  
 子視窗窗格的識別碼。  
  
### <a name="remarks"></a>備註  
 此成員函式用來建立 nonviews 的窗格，而且可能在呼叫之前窗格存在。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane  
 決定是否`pWnd`目前是子此分隔視窗窗格。  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)要測試的物件。  
  
 `pRow`  
 指標`int`用來儲存資料列數目。  
  
 `pCol`  
 指標`int`用來儲存資料行編號。  
  
### <a name="return-value"></a>傳回值  
 如果是非零值，`pWnd`目前是子此分隔視窗窗格，及`pRow`和`pCol`值隨即填入分隔視窗中窗格的位置。 如果`pWnd`不是子窗格的分隔視窗中，就會傳回 0。  
  
### <a name="remarks"></a>備註  
 在 Visual c + + 6.0 之前的版本，此函式定義為  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 此版本現在已過時，不應使用。  
  
##  <a name="istracking"></a>  CSplitterWnd::IsTracking  
 呼叫以判斷目前正在移動視窗中的分隔列是否此成員函式。  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>傳回值  
 如果分隔器作業正在進行中，則為非零否則便是 0。  
  
##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter  
 呈現分隔視窗的映像。  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 要在其中繪製的裝置內容的指標。 如果`pDC`是**NULL**，然後[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)稱為架構並沒有分割繪製視窗。  
  
 `nType`  
 值為**列舉 ESplitType**，它可以是下列其中之一：  
  
- **splitBox**分隔器拖曳方塊。  
  
- `splitBar` 出現兩個分割視窗之間的列。  
  
- **splitIntersection**分隔視窗的交集。 Windows 95/98 上執行時，將不會呼叫這個項目。  
  
- **splitBorder**分割視窗框線。  
  
 `rect`  
 若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定的大小和形狀分割視窗。  
  
### <a name="remarks"></a>備註  
 若要繪製指定的分隔視窗的確切特性架構會呼叫此成員函式。 覆寫`OnDrawSplitter`分隔視窗的不同圖形化元件圖像的進階自訂作業。 預設圖像是類似於 Microsoft 適用於 Windows 或 Microsoft Windows 95/98，在分隔器分隔列交集混合在一起。  
  
 如需動態分隔視窗的詳細資訊，請參閱 「 分隔視窗 」 文章中[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`類別概觀。  
  
##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker  
 呈現分隔視窗是相同大小與外型框架視窗的映像。  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 若要參考`CRect`物件，指定追蹤矩形。  
  
### <a name="remarks"></a>備註  
 此成員函式是由架構呼叫期間的分隔器調整大小。 覆寫`OnInvertTracker`分隔視窗的圖像的進階自訂作業。 預設圖像是類似於 Microsoft 適用於 Windows 或 Microsoft Windows 95/98，在分隔器分隔列交集混合在一起。  
  
 如需動態分隔視窗的詳細資訊，請參閱 「 分隔視窗 」 文章中[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`類別概觀。  
  
##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout  
 若要重新分隔視窗顯示調整資料列或資料行的大小之後呼叫。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以正確重新分隔視窗顯示之後已將調整資料列和資料行的大小與[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式。 如果分隔視窗會顯示之前，您可以變更在建立程序的一部分的資料列和資料行的大小，它不需要呼叫此成員函式。  
  
 每當使用者分隔視窗調整大小時，或移動分割時，架構會呼叫此成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例的[CSplitterWnd::SetColumnInfo](#setcolumninfo)。  
  
##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane  
 將框架中作用中的一個窗格的設定。  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `row`  
 如果`pWnd`是**NULL**，將會是作用中 窗格中指定的資料列。  
  
 `col`  
 如果`pWnd`是**NULL**，將會是作用中 窗格中指定的資料行。  
  
 `pWnd`  
 指標`CWnd`物件。 如果**NULL**，所指定的窗格`row`和`col`設定為使用中。 如果沒有**NULL**，指定已設定使用中 窗格。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫架構，以設定為使用中 窗格，當使用者將焦點變更為在框架視窗內的窗格。 您可以明確地呼叫`SetActivePane`若要將焦點變更為指定的檢視。  
  
 藉由提供資料列和資料行中，指定窗格**或**藉由提供`pWnd`。  
  
##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo  
 呼叫以設定所指定的資料行資訊。  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>參數  
 `col`  
 指定分隔視窗資料行。  
  
 *cxIdeal*  
 指定單位為像素的分隔視窗資料行的理想寬度。  
  
 `cxMin`  
 指定單位為像素的分隔視窗資料行的最小寬度。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式設定新的最小寬度及資料行的理想寬度。 資料行的最小值會判斷當資料行將被太小而無法完整顯示。  
  
 當架構顯示分隔視窗時，它會配置資料行，並根據其理想的維度，使用從左上角到右下角分隔視窗工作區的資料列中的窗格。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo  
 設定所指定的資料列資訊的呼叫。  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>參數  
 `row`  
 指定分隔視窗資料列。  
  
 *cyIdeal*  
 指定分隔視窗資料列的理想高度，單位為像素。  
  
 `cyMin`  
 指定分隔視窗資料列的最小高度，單位為像素。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以設定新的最小高度和資料列的理想高度。 資料列的最小值決定的資料列何時會太小而無法完整顯示。  
  
 當架構顯示分隔視窗時，它會配置資料行，並根據其理想的維度，使用從左上角到右下角分隔視窗工作區的資料列中的窗格。  
  
##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle  
 指定分隔視窗的新捲軸樣式共用捲軸的支援。  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 分隔視窗的新捲軸樣式共用捲軸的支援，它可以是下列值之一：  
  
- **WS_HSCROLL**建立/顯示水平共用捲軸。  
  
- **WS_VSCROLL**建立/顯示垂直共用捲軸。  
  
### <a name="remarks"></a>備註  
 一旦建立之後的捲軸它將不會終結即使`SetScrollStyle`呼叫沒有該樣式; 改用這些捲軸會隱藏。 這可讓保留其狀態，即使它們隱藏的捲軸。 在呼叫`SetScrollStyle`就必須呼叫[RecalcLayout](#recalclayout)的所有變更才會生效。  
  
##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn  
 指示框架視窗垂直分隔的位置為何。  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>參數  
 *cxBefore*  
 位置 （以像素分割之前）。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 建立垂直分隔視窗時，會呼叫此成員函式。 `SplitColumn` 指出分割發生的預設位置。  
  
 `SplitColumn` 由架構呼叫以實作動態分隔視窗的邏輯 (也就是如果分隔視窗具有**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="splitrow"></a>  CSplitterWnd::SplitRow  
 指示框架視窗水平分隔的位置為何。  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>參數  
 *cyBefore*  
 位置 （以像素分割之前）。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 建立水平分隔視窗時，會呼叫此成員函式。 `SplitRow` 指出分割發生的預設位置。  
  
 `SplitRow` 由架構呼叫以實作動態分隔視窗的邏輯 (也就是如果分隔視窗具有**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="ondraw"></a>  CSplitterWnd::OnDraw  
 由架構呼叫以繪製分隔視窗。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容的指標。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 VIEWEX](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)
