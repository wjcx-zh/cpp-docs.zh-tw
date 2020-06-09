---
title: 影像清單中的影像覆疊
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: 861bcd5165ad0938ae6bbd77fc4a9f09095ce789
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624481"
---
# <a name="image-overlays-in-image-lists"></a>影像清單中的影像覆疊

每個影像清單（[CImageList](reference/cimagelist-class.md)）都包含一份影像清單，可用來做為覆迭遮罩。 「覆疊遮罩」是一個以透明方式繪製在另一個影像上的影像。 所有影像都可以當做覆疊遮罩。 您最多可以為每個影像清單指定四個覆疊遮罩。

您可以使用[SetOverlayImage](reference/cimagelist-class.md#setoverlayimage)成員函式、影像的索引和覆迭遮罩的索引，將影像的索引新增至覆迭遮罩清單。 請注意，覆疊遮罩的索引是以一起始而不是以零起始。

您可以使用的單一呼叫，在影像上繪製覆迭遮罩 `Draw` 。 其中的參數包含影像的索引和繪製覆疊遮罩的索引。 您必須使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏來指定覆迭遮罩的索引。 呼叫[DrawIndirect](reference/cimagelist-class.md#drawindirect)成員函式時，您也可以指定重迭影像。

## <a name="see-also"></a>另請參閱

[使用 CImageList](using-cimagelist.md)<br/>
[控制項](controls-mfc.md)
