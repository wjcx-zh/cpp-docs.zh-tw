---
title: 使用映像清單 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc30d418ae57205e4566dad7f490a773321768e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391666"
---
# <a name="using-an-image-list"></a>使用影像清單

影像清單的典型用法會遵循下列模式：

- 建構[CImageList](../mfc/reference/cimagelist-class.md)物件，並呼叫其中一個多載其[建立](../mfc/reference/cimagelist-class.md#create)函式來建立映像清單，並將其附加至`CImageList`物件。

- 如果您未新增映像，當您在建立映像清單，將影像新增至影像清單，藉由呼叫[新增](../mfc/reference/cimagelist-class.md#add)或是[讀取](../mfc/reference/cimagelist-class.md#read)成員函式。

- 與控制項關聯的影像清單，藉由呼叫適當的成員函式，該控制項，或繪製影像的影像清單中使用影像清單的自行[繪製](../mfc/reference/cimagelist-class.md#draw)成員函式。

- 可能是可讓使用者拖曳影像，使用的拖曳影像清單的內建支援。

> [!NOTE]
>  如果您建立映像清單時**新**運算子，您必須銷毀`CImageList`物件時完成它。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)

