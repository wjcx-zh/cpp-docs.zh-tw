---
title: 影像清單中的影像覆疊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55a55a6e015a2f8c1613a85717c030737712c4da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="image-overlays-in-image-lists"></a>影像清單中的影像覆疊
每個影像清單 ([CImageList](../mfc/reference/cimagelist-class.md)) 包含用於覆疊遮罩的影像清單。 「覆疊遮罩」是一個以透明方式繪製在另一個影像上的影像。 所有影像都可以當做覆疊遮罩。 您最多可以為每個影像清單指定四個覆疊遮罩。  
  
 使用覆疊遮罩的清單新增影像索引[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)成員函式、 影像、 索引和覆疊遮罩的索引。 請注意，覆疊遮罩的索引是以一起始而不是以零起始。  
  
 您透過使用單一呼叫影像繪製覆疊遮罩**繪製**。 其中的參數包含影像的索引和繪製覆疊遮罩的索引。 您必須使用[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)巨集來指定覆疊遮罩的索引。 您也可以指定覆疊影像，當呼叫[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

