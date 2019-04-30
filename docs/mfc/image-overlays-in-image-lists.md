---
title: 影像清單中的影像覆疊
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: 8dd0b30ef29a48ebc763564e6fe23632cd300831
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407961"
---
# <a name="image-overlays-in-image-lists"></a>影像清單中的影像覆疊

每個影像清單 ([CImageList](../mfc/reference/cimagelist-class.md)) 包含用於覆疊遮罩的映像的清單。 「覆疊遮罩」是一個以透明方式繪製在另一個影像上的影像。 所有影像都可以當做覆疊遮罩。 您最多可以為每個影像清單指定四個覆疊遮罩。

利用覆疊遮罩清單新增影像之索引[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)成員函式、 一個影像的索引和覆疊遮罩的索引。 請注意，覆疊遮罩的索引是以一起始而不是以零起始。

您使用的單一呼叫影像繪製覆疊遮罩`Draw`。 其中的參數包含影像的索引和繪製覆疊遮罩的索引。 您必須使用[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)巨集來指定覆疊遮罩的索引。 您也可以呼叫時指定覆疊影像[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
