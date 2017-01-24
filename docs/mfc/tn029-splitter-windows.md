---
title: "TN029：分隔視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.windows.splitter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "分隔視窗, 關於分隔視窗"
  - "TN029"
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN029：分隔視窗
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註說明 MFC [CSplitterWnd Class](../mfc/reference/csplitterwnd-class.md)，提供視窗分割和管理調整其他窗格視窗。  
  
## 分隔器樣式  
 `CSplitterWnd` 支援分割的視窗兩個不同樣式。  
  
 在「靜態分隔」，建立時分隔視窗窗格建立。  窗格的順序和數目永遠不會變更。  分隔列來調整大小不同窗格。  您可以使用這個樣式中顯示每個窗格不同的檢視類別。  Visual C\+\+ 圖形編輯和 Windows 文件管理員是使用這個分隔器樣式程式的範例。  分隔視窗樣式不使用分隔器方塊。  
  
 在「動態分隔器」，當使用者分割和非分割新檢視，其他窗格建立和終結。  這個分隔器啟動以單一檢視並為使用者提供分隔器方塊啟始分割。  表示這個檢視某一方向時，分割分隔視窗動態建立一個新的檢視物件。  這個新的檢視物件表示新窗格。  使用鍵盤介面，如果檢視在兩個方向分割，分隔視窗建立三個新窗格的三個新的檢視物件。  當分割為作用中時，視窗會顯示分隔器方塊為在窗格之間的一個分隔列。  視窗終結其他檢視物件，當使用者移除分割時，不過，原始的檢視中，直到終結分隔視窗。  Microsoft Excel 和 Microsoft Word 是使用動態分隔樣式應用程式的範例。  
  
 當您建立任一類型分隔視窗時，您必須指定分隔器處理的最大資料列和資料行。  一個靜態分隔窗格會填入所有資料列和資料行。  建立 `CSplitterWnd` 時，一個動態分隔器將只會建立第一個窗格。  
  
 您可以為靜態分隔指定窗格的最大字元數是 16 x 16 資料行。  建議的組態是:  
  
-   資料行 1 x 2 行:通常與不同的窗格  
  
-   資料行 1 x 2 行:通常與不同的窗格  
  
-   資料行 2 x 2 行:通常與類似的窗格  
  
 您可以為動態分隔器指定窗格的最大字元數是 2 x 2 資料行。  建議的組態是:  
  
-   資料行 1 x 2 行:對於分欄式資料  
  
-   資料行 2 x 1 行:對於文字或其他資料。  
  
-   資料行 2 x 2 行:對於格線或資料表中的資料  
  
## 分隔器範例  
 許多 MFC 範例程式直接或間接使用分隔視窗。  一般 MFC 範例 [VIEWEX](../top/visual-cpp-samples.md) 在分隔器說明靜態分隔的數個用法，包括如何將分隔器。  
  
 您也可以使用 ClassWizard 建立包含分隔視窗的新的多重文件介面 \(MDI\) 子框架視窗類別。  如需分隔視窗的詳細資訊，請參閱 [許多資料型別、檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## 實作使用的詞彙  
 這是特定的到分隔視窗的詞彙清單:  
  
 `CSplitterWnd`:  
 提供分割窗格的控制項和捲軸共用資料列中的所有窗格或資料行之間的視窗。  您指定資料列和資料行的以零起始的數字 \(第一個窗格是資料行和資料列 \= 0 \= 0\)。  
  
 Pane:  
 `CSplitterWnd` 處理的特定的視窗。  窗格通常是從 [CView Class](../mfc/reference/cview-class.md)衍生的物件，不過，可以是有適當的子視窗 ID. 的 [CWnd](../mfc/reference/cwnd-class.md) 物件。  
  
 使用 `CWnd`衍生物件，請將物件的 `RUNTIME_CLASS` 和 `CreateView` 函式中，您會，如果您使用 `CView`衍生類別。  因為架構使用動態建立在執行階段，您的類別必須使用 `DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE` 。  雖然有專用的 `CView` 類別中 `CSplitterWnd` 的大量程式碼時，請一律使用 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md) ，在這些動作執行之前\)。  
  
 分隔列:  
 放置在窗格之間資料列和資料行的控制項。  它可以用來調整執行窗格大小或行。  
  
 分隔器方塊:  
 在您可以使用建立新窗格欄或列的動態 `CSplitterWnd` 控制項。  它位於垂直捲軸頂端或在水平捲軸左邊。  
  
 分隔器交集:  
 一個垂直分隔列和一個水平分隔列的交集。  您可以將它同時調整窗格資料列和資料行的大小。  
  
## 共用的捲軸。  
 `CSplitterWnd` 類別也支援共用的捲軸。  這些捲軸控制項是 `CSplitterWnd` 的子系和與在分隔器的不同窗格之間共用。  
  
 例如，在中，在建立 `CSplitterWnd`時，在第 1 x 2 行視窗，您可以指定 WS\_VSCROLL。  視窗建立共用在兩個窗格之間的特殊捲軸控制項。  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 當使用者移動捲軸， `WM_VSCROLL` 資訊傳送到兩個檢視。  當任一個檢視設定捲軸位置，共用捲軸將設定。  
  
 請注意共用捲軸是最有用的類似的檢視物件。  如果混合檢視不同輸入分隔器，則您可能需要撰寫特殊程式碼協調它們的捲動位置。  任何 `CView`\- `CWnd` 使用捲軸 API 的衍生類別會委派至共用捲軸，如果有的話。  `CScrollView` 實作不支援共用的捲軸 `CView` 類別的範例。  從 `CView`，類別不是衍生自非依賴控制項捲軸的類別，例如或使用標準 Windows 實作的類別 \( `CEditView`\)，不會與 `CSplitterWnd`搭配使用共用捲軸功能。  
  
## 最小大小  
 對於每個資料行具有資料列最低高度，，並針對每個資料行具有的最小寬度。  最小確保窗格不太小而無法顯示完整的詳細資料。  
  
 對於靜態分隔視窗，初始資料列最低高度和寬度為 0。  對於動態分隔視窗，初始資料列最低高度和寬度由 `CSplitterWnd::Create` 函式的 `sizeMin` 參數設定為。  
  
 使用 [CSplitterWnd::SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) 和 [CSplitterWnd::SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) 函式，您可以變更這些最小大小。  
  
## 實際的理想的大小  
 窗格的配置在分隔視窗的取決於包含這些框架的大小。  當使用者調整包含框架時， `CSplitterWnd` 重新定位和調整窗格，以便盡可能好相容。  
  
 使用者可以手動設定資料列高度和寬度大小，或使用 `CSplitterWnd` 類別，或者程式可以設定理想的大小。  實際大小大於理想可小或。  視窗會調整為實際大小，如果沒有足夠的空間顯示理想的大小，或有右邊分隔視窗的或下方的許多空白空間。  
  
## 自訂控制項  
 您可以覆寫許多函式提供自訂行為和自訂的介面。  您可以覆寫這個設定為分隔視窗的各種圖形元件提供替代成像。  
  
-   `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
-   `virtual void OnInvertTracker(const CRect& rect);`  
  
 您呼叫這個函式會建立共用捲軸控制項。  您可以覆寫它在捲軸旁邊建立額外的控制項。  
  
-   `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 這些函式實作動態分隔視窗的邏輯。  您可以覆寫這些提供更多進階的分隔器邏輯。  
  
-   `virtual void DeleteView(int row, int col);`  
  
-   `virtual BOOL SplitRow(int cyBefore);`  
  
-   `virtual BOOL SplitColumn(int cxBefore);`  
  
-   `virtual void DeleteRow(int rowDelete);`  
  
-   `virtual void DeleteColumn(int colDelete);`  
  
## CView 功能  
 `CView` 類別使用下列進階命令委派至 `CSplitterWnd` 實作。  由於這些命令是虛擬的，標準 `CView` 實作不需要整個 `CSplitterWnd` 實作連接點。  如需使用不是 `CView` ，但是 `CSplitterWnd`的應用程式， `CSplitterWnd` 實作的應用程式將無法連接。  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 確認 ID\_NEXT\_PANE 或 ID\_PREV\_PANE 目前是否可能的。  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 執行下一個窗格」或「上一個窗格」命令。  
  
 `virtual BOOL DoKeyboardSplit();`  
 執行鍵盤分割命令，通常是「被分隔視窗」。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)