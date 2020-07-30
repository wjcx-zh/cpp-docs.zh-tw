---
title: 使用影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 710831ea8ef6b52292ba3e8eb84a69575c6c7508
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226824"
---
# <a name="using-an-image-list"></a>使用影像清單

影像清單的一般用法會遵循下列模式：

- 建立[CImageList](../mfc/reference/cimagelist-class.md)物件，並呼叫其[create](../mfc/reference/cimagelist-class.md#create)函式的其中一個多載來建立影像清單，並將它附加至 `CImageList` 物件。

- 如果您在建立影像清單時未加入影像，請呼叫[add](../mfc/reference/cimagelist-class.md#add)或[Read](../mfc/reference/cimagelist-class.md#read)成員函式，將影像新增至影像清單。

- 藉由呼叫該控制項的適當成員函式，讓影像清單與控制項產生關聯，或使用影像清單的[draw](../mfc/reference/cimagelist-class.md#draw)成員函式，自行繪製影像清單中的影像。

- 可能允許使用者拖曳影像，使用影像清單的內建支援進行拖曳。

> [!NOTE]
> 如果影像清單是使用運算子建立的 **`new`** ，您必須在 `CImageList` 完成時終結物件。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
