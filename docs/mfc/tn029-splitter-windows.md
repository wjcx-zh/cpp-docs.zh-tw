---
title: TN029： 分隔器 Windows |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.windows.splitter
dev_langs:
- C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24556d7a331a74936631eef4fec2e293126cdbab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379514"
---
# <a name="tn029-splitter-windows"></a>TN029：分隔視窗

本提示描述 MFC [CSplitterWnd 類別](../mfc/reference/csplitterwnd-class.md)，其中提供視窗分割，並管理的其他窗格視窗調整大小。

## <a name="splitter-styles"></a>分隔器樣式

A`CSplitterWnd`支援分割 windows 的兩個不同的樣式。

在 「 靜態分隔器中，「 分隔器視窗會在建立時建立窗格。 永遠不會變更的順序和的窗格數目。 分隔器列用來調整大小的不同窗格。 您可以使用這個樣式，在每個窗格中顯示不同的檢視類別。 Visual c + + 圖形編輯器和 Windows 檔案管理員會使用這個分隔器樣式的程式的範例。 這種分隔器視窗樣式不會使用分隔器方塊。

在 「 動態分隔器，「 其他窗格建立，並終結做為使用者分割和取消分割新檢視上。 此分隔器開始的單一檢視，並提供使用者起始分割的分隔器方塊。 分隔器視窗會以單一方向分割檢視時，動態建立新的檢視物件。 這個新的檢視物件表示新的窗格。 如果兩個方向分割檢視所使用的鍵盤介面，分隔器視窗就會建立三個新檢視物件的三個新的窗格。 分割作用中時，Windows 會顯示在窗格之間的分隔器列分隔器方塊。 當使用者移除分割，但在原始檢視仍在分隔器視窗本身之前被終結時，Windows 就會終結其他檢視物件。 Microsoft Excel 和 Microsoft Word 所使用的動態分隔器樣式的應用程式的範例。

當您建立分隔器視窗的其中一種時，您必須指定資料列和分隔器會管理的資料行的最大數目。 靜態分隔器會建立以填滿所有資料列和資料行的窗格。 動態分隔器會建立第一個窗格時`CSplitterWnd`建立。

您可以指定靜態分隔器窗格的最大數目是由 16 個資料行的 16 個資料列。 建議的設定如下︰

- 1 個資料列 x 2 資料行： 通常會有不同的窗格

- 2 個資料列 x 1 資料行： 通常會有不同的窗格

- 2 個資料列 x 2 資料行： 通常會有類似的窗格

您可以指定動態分隔器中的窗格的最大數目是由 2 個資料行的 2 個資料列。 建議的設定如下︰

- 1 個資料列 x 2 資料行： 單欄式資料

- 2 個資料列 x 1 資料行： 文字或其他資料

- 2 個資料列 x 2 資料行： 方格或資料表導向資料

## <a name="splitter-examples"></a>分隔器範例

直接或間接，許多 MFC 範例程式會使用分隔視窗。 MFC 一般範例[VIEWEX](../visual-cpp-samples.md)說明幾種靜態分隔器，包括如何將分隔器放在分隔器的使用。

您也可以使用類別精靈來建立新的多個文件介面 (MDI) 子框架視窗類別，其中包含分隔器視窗。 如需有關分隔視窗的詳細資訊，請參閱[多個文件類型、 檢視和框架 Windows](../mfc/multiple-document-types-views-and-frame-windows.md)。

## <a name="terminology-used-by-implementation"></a>實作所使用的術語

以下是專屬於分隔視窗的詞彙的清單：

`CSplitterWnd`: 提供窗格分割控制項和所有窗格上的資料列或資料行之間共用的捲軸的視窗。 您可以指定資料列和資料行之以零起始的數字 (第一個窗格是資料列 = 0 且資料行 = 0)。

窗格中： 為特定應用程式視窗，`CSplitterWnd`管理。 一個窗格，通常是物件衍生自[CView 類別](../mfc/reference/cview-class.md)，但可以是任何[CWnd](../mfc/reference/cwnd-class.md)物件，具有適當的子視窗識別碼。

若要使用`CWnd`-衍生物件，則會傳遞至物件的 RUNTIME_CLASS`CreateView`函式，如果您使用如同`CView`-衍生的類別。 您的類別必須使用 DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE，因為架構會在執行階段中使用動態建立。 雖然有很多的程式碼`CSplitterWnd`專屬於`CView`類別[cobject:: Iskindof](../mfc/reference/cobject-class.md#iskindof)永遠會執行這些動作之前使用。

分隔器列： 資料列和資料行的窗格之間放置控制項。 它可用來調整大小的資料列或資料行的窗格。

分隔器方塊： 控制項中動態`CSplitterWnd`可用來建立新的資料列或資料行的窗格。 它是位於最上方的垂直捲軸或水平捲軸的左邊。

分隔器交集： 垂直分割列和水平分割列的交集。 您可以將它拖曳至同時調整的資料列和資料行 窗格的大小。

## <a name="shared-scroll-bars"></a>共用的捲軸

`CSplitterWnd`類別也支援共用的捲軸。 這些捲軸控制項是子系`CSplitterWnd`和分隔器中會共用以不同的窗格。

例如，在 1 個資料列 x 2 資料行 視窗中，您可以指定 WS_VSCROLL 建立時`CSplitterWnd`。 Windows 會建立特殊的捲軸控制項的兩個窗格之間共用。

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

當使用者移動捲軸時，WM_VSCROLL 訊息將會傳送至這兩個檢視。 當任一個檢視設定捲軸列位置時，將會設定共用的捲軸。

請注意，共用的捲軸最有用的類似的檢視物件。 如果您混用在分隔器中的不同類型的檢視，您可能必須撰寫特殊的程式碼，以協調其捲軸位置。 任何`CView`-衍生類別，以使用`CWnd`若有的話，Api 會委派至共用的捲軸的捲軸。 `CScrollView`實作，即是一例`CView`類別可支援共用捲軸。 不從衍生的類別`CView`，依賴非控制項捲軸的類別或使用標準的 Windows 實作的類別 (例如`CEditView`) 的 「 共用的捲軸列 」 功能不適用於`CSplitterWnd`。

## <a name="minimum-sizes"></a>最小的大小

每個資料列中，沒有最小資料列高度，而且每個資料行中，沒有最小的資料行寬度。 此最小值可確保不太小，無法顯示的完整的詳細資料 窗格。

靜態分隔視窗的初始最小的資料列的高度和資料行寬度會是 0。 動態分隔視窗的初始最小的資料列的高度和資料行寬度由設定*sizeMin*參數`CSplitterWnd::Create`函式。

您可以使用，以變更這些最小的大小[CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo)並[CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo)函式。

## <a name="actual-vs-ideal-sizes"></a>實際與。理想的大小

中的窗格分隔器視窗配置取決於包含它們之框架的大小。 當使用者調整包含的框架，`CSplitterWnd`重新定位和調整窗格的大小，使它們符合且盡可能。

使用者可以手動設定的資料列高度和資料行的寬度大小，或程式可以使用設定的理想大小`CSplitterWnd`類別。 實際大小是小於或大於理想。 如果沒有足夠空間可顯示的理想大小，或是否有太多空白空間上的權限或分隔器視窗的底部，Windows 會調整的實際大小。

## <a name="custom-controls"></a>自訂控制項

您可以覆寫許多函式，以提供自訂的行為及自訂的介面。 您可以覆寫此提供分隔器視窗的各種圖形化元件的替代影像的第一個集合。

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

您呼叫此函式來建立共用的捲軸控制項。 您可以覆寫，以便建立額外的控制項旁的捲軸。

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

這些函式實作動態分隔視窗的邏輯。 您可以覆寫這些檔案來提供更進階的分隔器邏輯。

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>CView 功能

`CView`類別會使用下列高層級的命令，來委派給`CSplitterWnd`實作。 這些命令是虛擬的因為標準`CView`實作不需要整個`CSplitterWnd`連結中的實作。 使用的應用程式`CView`而非`CSplitterWnd`，則`CSplitterWnd`實作不會與應用程式連結。

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   檢查是否有目前可能的 ID_NEXT_PANE 或 ID_PREV_PANE。

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   執行 「 下一個窗格 」 或 「 上一個窗格 」 的命令。

- `virtual BOOL DoKeyboardSplit();`

   執行鍵盤分隔的命令，通常是 「 分割視窗 」。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

