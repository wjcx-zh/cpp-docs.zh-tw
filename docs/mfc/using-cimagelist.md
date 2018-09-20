---
title: 使用 CImageList |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CImageList
dev_langs:
- C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ebfcb8fbacd3c464fc3697fc15bad385c1547d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420649"
---
# <a name="using-cimagelist"></a>使用 CImageList

影像清單，由類別[CImageList](../mfc/reference/cimagelist-class.md)，是相同大小的影像，其中每一個可以參考依其索引的集合。 影像清單用來有效管理大量圖示或點陣圖。 映像清單因為它們不是視窗，將本身不是控制項不過，它們會使用與許多不同類型的控制項，包括清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md))，樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))，以及索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。

在一個影像清單中的所有影像會以螢幕裝置格式包含在單一的寬點陣圖中。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 `CImageList` 提供成員函式，可讓您繪製影像、建立和終結影像清單、加入和移除影像、取代影像、合併影像和拖曳影像。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [影像清單的類型](../mfc/types-of-image-lists.md)

- [使用影像清單](../mfc/using-an-image-list.md)

- [管理影像清單](../mfc/manipulating-image-lists.md)

- [從影像清單描繪影像](../mfc/drawing-images-from-an-image-list.md)

- [影像清單中的影像覆疊](../mfc/image-overlays-in-image-lists.md)

- [從影像清單拖曳影像](../mfc/dragging-images-from-an-image-list.md)

- [影像清單中的影像資訊](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)

