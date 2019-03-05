---
title: 影像清單的類型
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: 939aad78b7cf8cca9c940bae11892d23dbb659cb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304752"
---
# <a name="types-of-image-lists"></a>影像清單的類型

有兩種類型的影像清單 ([CImageList](../mfc/reference/cimagelist-class.md)): 不對和遮罩。 「 非遮罩的影像清單 」 包含色彩的點陣圖，其中包含一或多個映像。 「 遮罩的影像清單 」 是由兩個相同大小的點陣圖所組成。 第一個是色彩的點陣圖，其中包含映像，而第二個是單色點陣圖，其中包含一系列遮罩，其中每個映像中的第一個點陣圖。

其中一個多載的`Create`成員函式會採用表示是否已遮罩影像清單的旗標。 （其他多載建立遮罩的影像清單）。

將非遮罩的影像繪製時，它只會複製到目標裝置內容;也就是它繪製停留裝置內容的現有的背景色彩。 繪製遮罩的影像時，在影像位元遮罩，通常產生的點陣圖中透明區域的目標裝置內容的背景色彩會透過顯示的位元結合。 繪製遮罩的影像時，您可以指定數個的繪製樣式。 例如，您可以指定映像可遞色，來指出所選取的物件。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
