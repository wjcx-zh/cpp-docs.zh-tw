---
title: 使用 CImageList
ms.date: 11/04/2016
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 09fd0e95ce2981afbebbfe10d87b26f88a7b5e13
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447232"
---
# <a name="using-cimagelist"></a>使用 CImageList

影像清單（以類別[CImageList](../mfc/reference/cimagelist-class.md)表示）是相同大小影像的集合，其中每一個都可以由其索引加以參考。 影像清單用來有效管理大量圖示或點陣圖。 影像清單本身不是視窗，因為它們不是 windows;不過，它們會搭配數種不同類型的控制項一起使用，包括清單控制項（[CListCtrl](../mfc/reference/clistctrl-class.md)）、樹狀控制項（[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）和索引標籤控制項（[CTabCtrl](../mfc/reference/ctabctrl-class.md)）。

在一個影像清單中的所有影像會以螢幕裝置格式包含在單一的寬點陣圖中。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 `CImageList` 提供成員函式，可讓您繪製影像、建立和終結影像清單、加入和移除影像、取代影像、合併影像和拖曳影像。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [影像清單的類型](../mfc/types-of-image-lists.md)

- [使用影像清單](../mfc/using-an-image-list.md)

- [管理影像清單](../mfc/manipulating-image-lists.md)

- [從影像清單描繪影像](../mfc/drawing-images-from-an-image-list.md)

- [影像清單中的影像覆疊](../mfc/image-overlays-in-image-lists.md)

- [從影像清單拖曳影像](../mfc/dragging-images-from-an-image-list.md)

- [影像清單中的影像資訊](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)
