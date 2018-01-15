---
title: "TN029： 分隔視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.windows.splitter
dev_langs: C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95b7db2678c03b0508a1507567f8bedcf243cd4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn029-splitter-windows"></a>TN029：分隔視窗
此提示描述 MFC [CSplitterWnd 類別](../mfc/reference/csplitterwnd-class.md)，這樣會提供分割視窗，並管理其他窗格視窗的調整大小。  
  
## <a name="splitter-styles"></a>分隔器樣式  
 A`CSplitterWnd`支援兩個不同的分割視窗樣式。  
  
 在 「 靜態分隔器中，"分隔視窗時，建立窗格就會建立。 永遠不會變更的順序和的窗格數目。 分隔器列用來調整大小的不同窗格。 您可以使用此樣式，在每個窗格中顯示不同的檢視類別。 Visual c + + 圖形編輯器和 Windows 檔案管理員會使用這個分隔器樣式的程式的範例。 這種樣式的分隔視窗不會使用分隔器方塊。  
  
 「 動態分隔器 」，在其他窗格會在建立及終結做為使用者分割和取消分割新檢視。 此分隔開頭的單一檢視，並提供使用者可以起始分割的分隔器方塊。 分隔視窗會以單一方向分割檢視時，動態建立新的檢視物件。 這個新的檢視物件表示新的窗格。 如果檢視使用的鍵盤介面分割兩個方向傳送，分隔視窗就會建立三個新檢視表物件的三個新的窗格。 分割使用中時，Windows 會顯示為窗格之間的分隔列分隔器方塊。 當使用者移除分割，但會終結原始檢視維持分隔視窗本身之前，Windows 會終結額外的檢視物件。 Microsoft Excel 和 Microsoft Word 所使用的動態分隔器樣式的應用程式的範例。  
  
 當您建立分隔視窗的任何一種時，您必須指定資料列和分隔器會管理的資料行的最大數目。 靜態分隔器會建立要填滿所有資料列和資料行的窗格。 動態分隔器會建立只有第一個窗格時`CSplitterWnd`建立。  
  
 您可以指定靜態分隔器窗格的最大數目為 16 個資料行的 16 個資料列。 建議的設定如下：  
  
-   1 個資料列 x 2 資料行： 通常會有不同的窗格  
  
-   2 個資料列 x 1 資料行： 通常會有不同的窗格  
  
-   2 個資料列 x 2 資料行： 通常會有類似的窗格  
  
 數個窗格，您可以指定動態分隔器的最大數目是由 2 個資料行的 2 個資料列。 建議的設定如下：  
  
-   1 個資料列 x 2 資料行： 單欄式資料  
  
-   2 個資料列 x 1 資料行： 文字或其他資料  
  
-   2 個資料列 x 2 資料行： 方格或資料表導向資料  
  
## <a name="splitter-examples"></a>分隔器範例  
 直接或間接，許多 MFC 範例程式會使用分隔視窗。 MFC 一般範例[VIEWEX](../visual-cpp-samples.md)說明靜態分隔器，包括如何放在分隔器分隔的數種用法。  
  
 您也可以使用類別精靈來建立新的多個文件介面 (MDI) 子框架視窗類別，其中包含分隔視窗。 如需有關分隔視窗的詳細資訊，請參閱[多重文件類型、 檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## <a name="terminology-used-by-implementation"></a>由實作所使用的詞彙  
 以下是專屬於分隔視窗的詞彙的清單：  
  
 `CSplitterWnd`：  
 提供分割窗格控制項和所有窗格上的資料列或資料行之間共用的捲軸的視窗。 您可以指定資料列和資料行以零為起始的數字 (第一個窗格是資料列 = 0 且資料行 = 0)。  
  
 窗格中：  
 特定應用程式視窗，`CSplitterWnd`管理。 窗格通常是衍生自物件[CView 類別](../mfc/reference/cview-class.md)，但可以是任何[CWnd](../mfc/reference/cwnd-class.md)具有適當的子視窗識別碼。  
  
 若要使用`CWnd`-衍生物件，傳遞`RUNTIME_CLASS`之物件的`CreateView`函式，如果您使用，就像`CView`-衍生的類別。 您的類別必須使用`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`因為架構會在執行階段使用動態建立。 雖然有很多的程式碼`CSplitterWnd`專屬於`CView`類別[cobject:: Iskindof](../mfc/reference/cobject-class.md#iskindof)一律使用之前執行這些動作。  
  
 分隔列：  
 位於資料列和資料行的窗格控制項。 它可用來調整大小的資料列或資料行的窗格。  
  
 分隔器方塊：  
 在動態控制項`CSplitterWnd`可用來建立新的資料列或資料行的窗格。 它位於最上方的垂直捲軸或水平捲軸的左邊。  
  
 分隔器交集：  
 垂直分割列和水平分割列的交集。 您可以將它拖曳至同時調整的資料列和資料行的窗格大小。  
  
## <a name="shared-scroll-bars"></a>共用的捲軸  
 `CSplitterWnd`類別也可支援共用的捲軸。 這些捲軸控制項是子系`CSplitterWnd`，用來分隔在不同窗格與共用。  
  
 例如，在 1 個資料列 x 2 資料行視窗中，您可以指定 WS_VSCROLL 建立時`CSplitterWnd`。 Windows 會建立特殊的捲軸的兩個窗格之間共用。  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 當使用者將捲軸，`WM_VSCROLL`會將訊息傳送至這兩個檢視。 當任一個檢視設定捲軸列的位置時，將會設定共用的捲軸。  
  
 請注意，共用的捲軸最有用的類似的檢視物件。 如果您混在分隔器的不同類型的檢視，您可能必須撰寫特殊的程式碼，以協調其捲動位置。 任何`CView`-衍生的類別使用`CWnd`捲軸，如果存在的話，將會委派給共用的捲軸的應用程式開發介面。 `CScrollView`實作是一種`CView`類別支援共用的捲軸。 不從衍生的類別`CView`，依賴非控制項捲軸的類別或使用標準的 Windows 實作的類別 (例如， `CEditView`) 的共用的捲軸列功能不適用於`CSplitterWnd`。  
  
## <a name="minimum-sizes"></a>大小的下限。  
 每個資料列中，沒有最小資料列高度，而每個資料行沒有資料行寬度下限。 此最小值可確保不太小，無法顯示的完整的詳細資料 窗格。  
  
 靜態分隔視窗的初始最小資料列的高度和資料行寬度是 0。 動態分隔視窗的初始最小資料列的高度和資料行寬度由設定`sizeMin`參數`CSplitterWnd::Create`函式。  
  
 您可以使用，以變更這些最小大小[CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo)和[CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo)函式。  
  
## <a name="actual-vs-ideal-sizes"></a>實際的 vs。理想的大小  
 分隔視窗的窗格的配置取決於包含這些框架的大小。 當使用者調整為包含的框架，`CSplitterWnd`重新定位並調整窗格的大小，使它們符合且盡可能。  
  
 使用者可以手動設定的資料列高度和資料行寬度的大小，或程式可以使用設定的理想大小`CSplitterWnd`類別。 在實際大小可能會小於或大於最理想的。 如果沒有足夠空間可顯示理想大小，或如果沒有太多空白空間上的權限或分隔視窗的底部，Windows 會調整的實際大小。  
  
## <a name="custom-controls"></a>自訂控制項  
 您可以覆寫許多功能，以提供自訂的行為和自訂的介面。 您可以覆寫這個第一組提供替代圖像的分隔視窗的各種圖形化元件。  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
 您呼叫此函式以建立共用的捲軸控制項。 您可以覆寫它，以建立額外的控制項捲軸旁邊。  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 這些函式實作動態分隔視窗的邏輯。 您可以覆寫這些檔案來提供更進階的分隔器邏輯。  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>CView 功能  
 `CView`類別會使用下列的高層級命令來委派給`CSplitterWnd`實作。 這些命令都是虛擬的因為標準`CView`實作時，不需要將整個`CSplitterWnd`連結中的實作。 使用的應用程式`CView`但不是`CSplitterWnd`、`CSplitterWnd`實作將不會連結到應用程式。  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 檢查是否有目前可能的 ID_NEXT_PANE 或 ID_PREV_PANE。  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 執行 「 下一步 窗格"上一個窗格"命令。  
  
 `virtual BOOL DoKeyboardSplit();`  
 執行鍵盤分隔的命令，通常是 「 視窗分割 」。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

