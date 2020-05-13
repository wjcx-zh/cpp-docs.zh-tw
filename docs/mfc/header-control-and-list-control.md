---
title: 標題控制項和清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370477"
---
# <a name="header-control-and-list-control"></a>標題控制項和清單控制項

在大多數情況下,您將使用嵌入在[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView](../mfc/reference/clistview-class.md)物件中的標頭控制件。 但是,在某些情況下,需要單獨的標頭控件物件,例如操作以列或行排列的數據,位於[CView](../mfc/reference/cview-class.md)派生的物件中。 在這些情況下,您需要更好地控制嵌入式標頭控制件的外觀和默認行為。

在希望標頭控制件提供標準預設行為的常見情況下,您可能需要改用[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView。](../mfc/reference/clistview-class.md) 當`CListCtrl`您想要默認標頭控制件的功能時使用,該功能嵌入到清單檢視公共控制項中。 當您希望嵌入在檢視物件中的預設標頭控制件的功能時,請使用[CListView。](../mfc/reference/clistview-class.md)

> [!NOTE]
> 僅當使用**LVS_REPORT**樣式創建列表檢視控制項時,這些控制項才包括內建標頭控制件。

在大多數情況下,可以通過更改包含列表視圖控件的樣式來修改嵌入標頭控制元件的外觀。 此外,還可以通過父列表視圖控件的成員函數獲取有關標頭控件的資訊。 但是,為了對嵌入標頭控制的屬性和樣式進行完全控制和訪問,建議獲取指向標頭控制件物件的指標。

可以從任一`CListCtrl``CListView`或調用相應`GetHeaderCtrl`類 的成員函數訪問嵌入的標頭控制物件。 下列程式碼將示範此作業：

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [將影像清單與標題控制項一起使用](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
