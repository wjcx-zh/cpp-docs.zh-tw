---
title: "CSplitterWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- static splitter windows
- multiple views
- splitter windows
- views, multiple per frame
- dynamic splitter windows
- CSplitterWnd class
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d015aa604c5394ccbe8c7471b70c84763cc00a5b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="csplitterwnd-class"></a>CSplitterWnd 類別
提供分割視窗 (這是包含多個窗格的視窗) 的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|呼叫建構`CSplitterWnd`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|執行下一個窗格或上一個窗格的命令。|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|檢查是否為目前的下一個窗格或上一個窗格的命令。|  
|[CSplitterWnd::Create](#create)|若要建立動態分隔視窗，並將其附加至呼叫`CSplitterWnd`物件。|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|建立共用的捲軸。|  
|[CSplitterWnd::CreateStatic](#createstatic)|若要建立靜態分隔視窗，並將其附加至呼叫`CSplitterWnd`物件。|  
|[CSplitterWnd::CreateView](#createview)|呼叫可建立在分隔視窗中的窗格。|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|分隔視窗中刪除資料行。|  
|[CSplitterWnd::DeleteRow](#deleterow)|刪除資料列從分隔視窗。|  
|[CSplitterWnd::DeleteView](#deleteview)|刪除檢視從分隔視窗。|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|執行鍵盤分隔的命令，通常是 「 視窗分割 」。|  
|[CSplitterWnd::DoScroll](#doscroll)|執行同步的分隔視窗捲動。|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|捲動分隔視窗的特定像素數目。|  
|[CSplitterWnd::GetActivePane](#getactivepane)|決定從焦點或框架中的使用中檢視作用中的窗格。|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|傳回目前窗格資料行計數。|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|傳回指定之資料行的相關資訊。|  
|[CSplitterWnd::GetPane](#getpane)|傳回在指定的資料列和資料行的窗格。|  
|[CSplitterWnd::GetRowCount](#getrowcount)|傳回目前的窗格中的資料列計數。|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|傳回指定之資料列的相關資訊。|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|傳回共用的捲軸樣式。|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|傳回的子視窗窗格中，指定資料列及資料行識別碼。|  
|[CSplitterWnd::IsChildPane](#ischildpane)|若要判斷視窗是否目前子視窗的窗格此分隔器呼叫。|  
|[CSplitterWnd::IsTracking](#istracking)|判斷目前正在移動分隔器列是否。|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|若要重新分割視窗顯示調整資料列或資料行的大小之後呼叫。|  
|[CSplitterWnd::SetActivePane](#setactivepane)|將作用中的一個框架中窗格的設定。|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|呼叫以設定指定之資料行資訊。|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|設定指定的資料列資訊的呼叫。|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|指定新的捲軸樣式的分隔視窗共用捲軸的支援。|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|表示框架視窗，以垂直方式分割。|  
|[CSplitterWnd::SplitRow](#splitrow)|表示框架視窗水平分割的位置。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|若要繪製分隔視窗架構呼叫。|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|呈現分隔視窗的影像。|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|會轉譯為相同的大小和形狀與框架視窗的分隔視窗的映像。|  
  
## <a name="remarks"></a>備註  
 窗格通常是一個應用程式特定物件衍生自[CView](../../mfc/reference/cview-class.md)，但它可以是任何[CWnd](../../mfc/reference/cwnd-class.md)具有適當的子視窗識別碼。  
  
 A`CSplitterWnd`物件通常內嵌在父代[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件。 建立`CSplitterWnd`物件使用下列步驟︰  
  
1.  內嵌`CSplitterWnd`父框架中的成員變數。  
  
2.  覆寫父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。  
  
3.  從內覆寫`OnCreateClient`，呼叫[建立](#create)或[CreateStatic](#createstatic)成員函式`CSplitterWnd`。  
  
 呼叫**建立**成員函式來建立動態分隔視窗。 動態分隔視窗通常用來建立及捲動的個別窗格或檢視表相同的文件數目。 架構會自動建立初始的窗格，分隔器;然後架構會建立、 調整大小，並處置其他窗格與使用者分隔視窗的控制項。  
  
 當您呼叫**建立**，指定最小資料列高度和資料行寬度，以決定何時太小，無法完全顯示的窗格。 在您呼叫後**建立**，您可以調整這些最小值，藉由呼叫[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函式。  
  
 也使用`SetColumnInfo`和`SetRowInfo`成員函式，以設定 「 適合 」 的資料行之間 「 適合 」 的資料列。 時，架構會顯示分割視窗中，它會先顯示父框架，然後分割視窗。 架構會再配置中資料行和資料列，根據其理想的維度，從左上角設法分隔視窗的工作區的右下角的窗格。  
  
 動態分隔視窗中的所有窗格都必須是相同的類別。 熟悉支援動態分隔視窗的應用程式包括 Microsoft Word 和 Microsoft Excel。  
  
 使用`CreateStatic`成員函式來建立靜態分隔視窗。 使用者可以變更靜態分隔視窗中，其數目或順序不使用中窗格的大小。  
  
 當您建立靜態分割時，您必須特別建立的所有靜態分割的窗格。 請確定您建立父框架之前的所有窗格`OnCreateClient`成員函式會傳回，否則架構會無法正確顯示視窗。  
  
 `CreateStatic`成員函式會自動初始化靜態分隔器的最小資料列高度和資料行寬度為 0。 在您呼叫後**建立**，調整這些最小值，藉由呼叫[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成員函式。 也使用`SetColumnInfo`和`SetRowInfo`呼叫之後`CreateStatic`，表示需要理想窗格維度。  
  
 靜態分隔器的個別窗格通常屬於不同的類別。 靜態分隔視窗的範例，請參閱圖形編輯器和 Windows 檔案管理員。  
  
 分隔視窗支援特殊的捲軸 （除了窗格可能會有的捲軸）。 這些捲軸是目的子系`CSplitterWnd`物件，並與窗格共用。  
  
 當您建立分隔視窗時，您可以建立這些特殊的捲軸。 例如，`CSplitterWnd`具有一個資料列中，兩個資料行，而**WS_VSCROLL**樣式會顯示垂直捲軸的兩個窗格。 當使用者將捲軸，`WM_VSCROLL`訊息都會傳送給這兩個窗格。 當窗格設定捲軸位置時，則會設定共用的捲軸。  
  
 如需分隔視窗的詳細資訊，請參閱︰  
  
- [技術提示 29](../../mfc/tn029-splitter-windows.md)  
  
-   知識庫文件 Q262024︰ 如何︰ 使用 CPropertySheet 為 CSplitterWnd 子  
  
 如需有關如何建立動態分隔視窗的詳細資訊，請參閱︰  
  
-   MFC 範例[Scribble](../../visual-cpp-samples.md)  
  
-   MFC 範例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="activatenext"></a>CSplitterWnd::ActivateNext  
 若要執行下一個窗格或上一個窗格的命令，架構呼叫。  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bPrev`  
 表示啟用哪一個視窗。 **TRUE**的前一個。**FALSE**的下一步。  
  
### <a name="remarks"></a>備註  
 此成員函式是高層級的命令，可由[CView](../../mfc/reference/cview-class.md)類別委派給`CSplitterWnd`實作。  
  
##  <a name="canactivatenext"></a>CSplitterWnd::CanActivateNext  
 若要查看是否下一個窗格或上一個窗格命令目前的架構呼叫。  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bPrev`  
 表示啟用哪一個視窗。 **TRUE**的前一個。**FALSE**的下一步。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式是高層級的命令，可由[CView](../../mfc/reference/cview-class.md)類別委派給`CSplitterWnd`實作。  
  
##  <a name="create"></a>CSplitterWnd::Create  
 若要建立動態分隔視窗中，呼叫**建立**成員函式。  
  
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
 分隔視窗中的資料列的數目上限。 此值不可超過 2。  
  
 *nMaxCols*  
 分隔視窗中的資料行的數目上限。 此值不可超過 2。  
  
 `sizeMin`  
 指定可能的顯示窗格中的最小大小。  
  
 `pContext`  
 指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 在大部分情況下，這可以是`pContext`傳遞給父框架視窗。  
  
 `dwStyle`  
 指定的視窗樣式。  
  
 `nID`  
 視窗的子視窗識別碼。 識別碼可以是**AFX_IDW_PANE_FIRST**除非分隔視窗是否位於另一個分隔視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以將內嵌`CSplitterWnd`父系[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件採取下列步驟︰  
  
1.  內嵌`CSplitterWnd`父框架中的成員變數。  
  
2.  覆寫父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成員函式。  
  
3.  呼叫**建立**的覆寫的成員函式`OnCreateClient`。  
  
 當您建立分隔視窗從父範圍內時，傳遞父框架`pContext`分隔視窗的參數。 否則，這個參數可以是**NULL**。  
  
 動態分隔視窗的初始最小資料列高度和資料行寬度由設定`sizeMin`參數。 這些最小值，判斷是否有太小，無法完整顯示 窗格，可以變更與[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式。  
  
 如需動態分隔視窗的詳細資訊，請參閱 「 分隔視窗 」 文件中[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`類別概觀。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&125;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl  
 若要建立共用的捲軸控制項架構呼叫。  
  
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
 覆寫`CreateScrollBarCtrl`包含額外的控制項，捲軸旁邊。 預設行為是建立標準 Windows 捲軸控制項。  
  
##  <a name="createstatic"></a>CSplitterWnd::CreateStatic  
 若要建立靜態分隔視窗中，呼叫`CreateStatic`成員函式。  
  
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
 A`CSplitterWnd`通常會內嵌在父代`CFrameWnd`或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)物件採取下列步驟︰  
  
1.  內嵌`CSplitterWnd`父框架中的成員變數。  
  
2.  覆寫父框架`OnCreateClient`成員函式。  
  
3.  呼叫`CreateStatic`的覆寫的成員函式[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。  
  
 靜態分隔視窗包含固定的數目的窗格中，通常來自於不同的類別。  
  
 當您建立靜態分隔視窗中時，您必須同時建立其所有窗格。 [CreateView](#createview)成員函式通常用於此目的，但是您可以建立其他 nonview 類別。  
  
 靜態分隔視窗的初始最小資料列高度和資料行寬度為 0。 這些最小值，判斷太小，無法完整顯示 窗格時，可以變更與[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式。  
  
 若要將捲軸加入至靜態分隔視窗中，加入**WS_HSCROLL**和**WS_VSCROLL**樣式來`dwStyle`。  
  
 請參閱 「 分隔器 Windows 」 中文章[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`類別概觀如需靜態分隔視窗。  
  
##  <a name="createview"></a>CSplitterWnd::CreateView  
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
 指定[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的新檢視。  
  
 *sizeInit*  
 指定新檢視的初始大小。  
  
 `pContext`  
 建立內容，用來建立檢視的指標 (通常是`pContext`傳遞給父框架的覆寫[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)建立分隔視窗的成員函式)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 必須先建立所有的靜態分隔視窗的窗格，架構會顯示在分隔器。  
  
 架構也會呼叫此成員函式 窗格中，資料列或資料行，會將分割動態分隔視窗的使用者時，建立新的窗格。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&4;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd  
 呼叫建構`CSplitterWnd`物件。  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>備註  
 建構`CSplitterWnd`兩個步驟中的物件。 首先，呼叫建構函式，建立`CSplitterWnd`物件，然後再呼叫[建立](#create)成員函式，建立分隔視窗並將它附加`CSplitterWnd`物件。  
  
##  <a name="deletecolumn"></a>CSplitterWnd::DeleteColumn  
 分隔視窗中刪除資料行。  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>參數  
 *colDelete*  
 指定要刪除的資料行。  
  
### <a name="remarks"></a>備註  
 若要實作動態分隔視窗的邏輯架構會呼叫此成員函式 (亦即是否已分隔視窗**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="deleterow"></a>CSplitterWnd::DeleteRow  
 刪除資料列從分隔視窗。  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>參數  
 *rowDelete*  
 指定要刪除的資料列。  
  
### <a name="remarks"></a>備註  
 若要實作動態分隔視窗的邏輯架構會呼叫此成員函式 (亦即是否已分隔視窗**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="deleteview"></a>CSplitterWnd::DeleteView  
 刪除檢視從分隔視窗。  
  
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
 如果刪除使用中檢視時，[下一步] 檢視會變成作用中。 預設實作會假設此檢視將會自動刪除[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)。  
  
 若要實作動態分隔視窗的邏輯架構會呼叫此成員函式 (亦即是否已分隔視窗**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit  
 執行鍵盤分隔的命令，通常是 「 視窗分割 」。  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式是高層級的命令，可由[CView](../../mfc/reference/cview-class.md)類別委派給`CSplitterWnd`實作。  
  
##  <a name="doscroll"></a>CSplitterWnd::DoScroll  
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
 捲軸程式碼，指出使用者的捲動要求。 這個參數由兩個部分組成︰ 低序位位元組，這會決定捲動發生水平的型別，以及高序位位元組，這會決定捲動發生垂直的型別︰  
  
- **SB_BOTTOM**向下捲動。  
  
- **SB_LINEDOWN**向下捲動一行。  
  
- **SB_LINEUP**向上捲動一行。  
  
- **SB_PAGEDOWN**向下捲動一頁。  
  
- **SB_PAGEUP**向上捲動一頁。  
  
- **SB_TOP**捲動至最上方。  
  
 `bDoScroll`  
 判斷是否發生指定的捲動動作。 如果`bDoScroll`是**TRUE** （也就是子視窗存在，而且如果分割視窗已捲軸範圍），然後指定捲動動作可以; 如果`bDoScroll`是**FALSE** （也就是說，如果沒有子視窗存在，或分割檢視也提供任何捲動範圍），則不會捲動。  
  
### <a name="return-value"></a>傳回值  
 非零，如果發生同步捲動;否則為 0。  
  
### <a name="remarks"></a>備註  
 執行同步的捲動分割視窗檢視收到捲動訊息時，架構會呼叫此成員函式。 需要使用者動作，才能允許進行同步處理捲動的覆寫。  
  
##  <a name="doscrollby"></a>CSplitterWnd::DoScrollBy  
 捲動分隔視窗的特定像素數目。  
  
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
 水平及垂直捲動的像素數目。  
  
 bDoScroll  
 判斷是否發生指定的捲動動作。 如果`bDoScroll`是**TRUE** （也就是子視窗存在，而且如果分割視窗已捲軸範圍），然後指定捲動動作可以; 如果`bDoScroll`是**FALSE** （也就是說，如果沒有子視窗存在，或分割檢視也提供任何捲動範圍），則不會捲動。  
  
### <a name="return-value"></a>傳回值  
 非零，如果發生同步捲動;否則為 0。  
  
### <a name="remarks"></a>備註  
 捲動訊息回應的架構會呼叫此成員函式、 執行同步處理量，單位為像素，以分割視窗捲動`sizeScroll`。 正值表示捲動往下及往右。負值表示向上及向左捲動。  
  
 需要使用者動作後才允許捲軸的覆寫。  
  
##  <a name="getactivepane"></a>CSplitterWnd::GetActivePane  
 決定從焦點或框架中的使用中檢視作用中的窗格。  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pRow`  
 指標**int**來擷取使用中 窗格中的資料列數目。  
  
 `pCol`  
 指標**int**來擷取使用中 窗格中的資料行數目。  
  
### <a name="return-value"></a>傳回值  
 使用中窗格的指標。 **NULL**有任何作用中的窗格。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫架構，以便判斷在分隔視窗中 [作用中的] 窗格。 需要使用者動作才可以取得使用中窗格的覆寫。  
  
##  <a name="getcolumncount"></a>CSplitterWnd::GetColumnCount  
 傳回目前窗格資料行計數。  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在分隔器會傳回目前的資料行數目。 靜態分隔器，這也會是資料行數目上限。  
  
##  <a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo  
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
 參考`int`設為目前的資料行寬度。  
  
 `cxMin`  
 參考`int`設為目前資料行的最小寬度。  
  
##  <a name="getpane"></a>CSplitterWnd::GetPane  
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
 傳回在指定的資料列和資料行的窗格。 通常是傳回的窗格[CView](../../mfc/reference/cview-class.md)-衍生的類別。  
  
##  <a name="getrowcount"></a>CSplitterWnd::GetRowCount  
 傳回目前的窗格中的資料列計數。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 分隔視窗中會傳回目前的列數。 靜態分隔視窗中，這也會是資料列的數目上限。  
  
##  <a name="getrowinfo"></a>CSplitterWnd::GetRowInfo  
 傳回指定之資料列的相關資訊。  
  
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
 若要參考`int`設為目前的像素為單位的資料列的高度。  
  
 `cyMin`  
 若要參考`int`設為目前的最小高度，單位為像素的資料列。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式可取得指定的資料列的相關資訊。 `cyCur`參數會填入目前指定的資料列的高度和`cyMin`填滿的資料列的最小高度。  
  
##  <a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle  
 傳回針對分隔視窗共用的捲軸樣式。  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一或多個下列的視窗樣式旗標，如果成功︰  
  
- **WS_HSCROLL**如果分隔器目前負責管理共用水平捲軸。  
  
- **WS_VSCROLL**如果分隔器目前負責管理共用的垂直捲軸。  
  
 如果為零，分隔視窗目前沒有管理任何共用的捲軸。  
  
##  <a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol  
 取得子系所指定的資料列及資料行 窗格的視窗 ID。  
  
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
 [!code-cpp[NVC_MFCWindowing #&5;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>CSplitterWnd::IsChildPane  
 決定是否`pWnd`正在子這個分隔視窗窗格。  
  
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
 如果是非零值，`pWnd`是目前的分割視窗中，子窗格和`pRow`和`pCol`填入窗格的分隔視窗中的位置。 如果`pWnd`不是子窗格的分隔視窗中，則傳回 0。  
  
### <a name="remarks"></a>備註  
 在 Visual c + + 6.0 之前的版本，此函式定義為  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 此版本現在已過時，並且不應使用。  
  
##  <a name="istracking"></a>CSplitterWnd::IsTracking  
 呼叫此成員函式，來判斷是否分隔列在視窗中目前正在移動。  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>傳回值  
 分隔作業正在進行中; 如果為非零否則為 0。  
  
##  <a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter  
 呈現分隔視窗的影像。  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 若要在其中繪製的裝置內容指標。 如果`pDC`是**NULL**，然後[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)稱為繪製架構並沒有分割視窗。  
  
 `nType`  
 值為**列舉 ESplitType**，它可以是下列其中之一︰  
  
- **splitBox**分隔器拖曳的方塊。  
  
- `splitBar`兩個分割視窗之間出現的列。  
  
- **splitIntersection**分隔視窗的交集。 在 Windows 95/98 上執行時，將不會呼叫這個項目。  
  
- **splitBorder**分割視窗框線。  
  
 `rect`  
 參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定的大小和形狀的分隔視窗。  
  
### <a name="remarks"></a>備註  
 此成員函式會呼叫架構，以便繪製，並且指定確切的分隔視窗的特性。 覆寫`OnDrawSplitter`分隔視窗的不同圖形化元件圖像的進階自訂作業。 預設圖像會很類似 Microsoft 適用於 Windows 或 Microsoft Windows 95/98 中，在分隔器中的分隔器列交集會混合在一起。  
  
 如需動態分隔視窗的詳細資訊，請參閱 「 分隔視窗 」 文件中[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`類別概觀。  
  
##  <a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker  
 會轉譯為相同的大小和形狀與框架視窗的分隔視窗的映像。  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 若要參考`CRect`物件，指定追蹤的矩形。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此成員函式的分隔器調整大小期間。 覆寫`OnInvertTracker`分隔視窗圖像的進階自訂作業。 預設圖像會很類似 Microsoft 適用於 Windows 或 Microsoft Windows 95/98 中，在分隔器中的分隔器列交集會混合在一起。  
  
 如需動態分隔視窗的詳細資訊，請參閱 「 分隔視窗 」 文件中[多重文件類型、 檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技術附註 29](../../mfc/tn029-splitter-windows.md)，而`CSplitterWnd`類別概觀。  
  
##  <a name="recalclayout"></a>CSplitterWnd::RecalcLayout  
 若要重新分割視窗顯示調整資料列或資料行的大小之後呼叫。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以正確重新分割視窗顯示後調整資料列和資料行的大小和[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成員函式。 如果分割視窗中顯示之前，您可以變更建立程序的一部分的資料列和資料行的大小，它就不需要呼叫此成員函式。  
  
 每當使用者分隔視窗的調整大小或移動分割時，架構會呼叫此成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例[CSplitterWnd::SetColumnInfo](#setcolumninfo)。  
  
##  <a name="setactivepane"></a>CSplitterWnd::SetActivePane  
 將作用中的一個框架中窗格的設定。  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `row`  
 如果`pWnd`是**NULL**，在窗格中，都可使用指定的資料列。  
  
 `col`  
 如果`pWnd`是**NULL**，在窗格中，都可使用指定的資料行。  
  
 `pWnd`  
 指標`CWnd`物件。 如果**NULL**，所指定的窗格`row`和`col`設定為使用中。 如果不是**NULL**，指定已設定使用中 窗格。  
  
### <a name="remarks"></a>備註  
 當使用者將焦點變更至框架視窗內的窗格，設定為使用中 窗格的架構會呼叫此成員函式。 您可以明確呼叫`SetActivePane`，將焦點變更至指定的檢視。  
  
 提供資料列和資料行，以指定窗格**或**藉由提供`pWnd`。  
  
##  <a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo  
 呼叫以設定指定之資料行資訊。  
  
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
 指定單位為像素的分隔器 視窗中的資料行的理想寬度。  
  
 `cxMin`  
 指定單位為像素的分隔器 視窗中的資料行的最小寬度。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，來設定新的最小寬度及資料行的理想寬度。 資料行的最小值會決定何時會太小，無法完全顯示的資料行。  
  
 當架構顯示分隔視窗時，它會配置中資料行和資料列，根據其理想的維度，從左上角設法分隔視窗的工作區的右下角的窗格。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&6;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>CSplitterWnd::SetRowInfo  
 設定指定的資料列資訊的呼叫。  
  
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
 呼叫此成員函式，來設定新的最小高度和資料列的理想高度。 資料列的最小值會決定何時會太小，無法完全顯示的資料列。  
  
 當架構顯示分隔視窗時，它會配置中資料行和資料列，根據其理想的維度，從左上角設法分隔視窗的工作區的右下角的窗格。  
  
##  <a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle  
 指定新的捲軸樣式的分隔視窗共用捲軸的支援。  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 分隔視窗的新捲軸樣式共用捲軸的支援，這可以是下列值之一︰  
  
- **WS_HSCROLL**建立/顯示水平共用捲軸。  
  
- **WS_VSCROLL**建立/顯示垂直共用捲軸。  
  
### <a name="remarks"></a>備註  
 一旦建立捲軸它將不會終結即使`SetScrollStyle`呼叫時沒有該樣式，改為那些捲軸會隱藏。 這可讓保留其狀態，即使它們隱藏的捲軸。 在呼叫`SetScrollStyle`就必須呼叫[RecalcLayout](#recalclayout)的所有變更才會生效。  
  
##  <a name="splitcolumn"></a>CSplitterWnd::SplitColumn  
 表示框架視窗，以垂直方式分割。  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>參數  
 *cxBefore*  
 像素為單位，之前在分割中的位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 建立垂直分割視窗時，會呼叫此成員函式。 `SplitColumn`指出發生分割的預設位置。  
  
 `SplitColumn`若要實作動態分隔視窗的邏輯架構會呼叫 (亦即是否已分隔視窗**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="splitrow"></a>CSplitterWnd::SplitRow  
 表示框架視窗水平分割的位置。  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>參數  
 *cyBefore*  
 像素為單位，之前在分割中的位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 建立的水平分隔視窗時，會呼叫此成員函式。 `SplitRow`指出發生分割的預設位置。  
  
 `SplitRow`若要實作動態分隔視窗的邏輯架構會呼叫 (亦即是否已分隔視窗**SPLS_DYNAMIC_SPLIT**樣式)。 您可以加以自訂，以及虛擬函式[CreateView](#createview)，以實作更進階的動態分隔器。  
  
##  <a name="ondraw"></a>CSplitterWnd::OnDraw  
 若要繪製分隔視窗架構呼叫。  
  
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

