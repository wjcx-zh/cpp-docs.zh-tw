---
title: "影像清單中的影像覆疊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e70365040b5f009e634a4867a4a1f974d47bd61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="image-overlays-in-image-lists"></a>影像清單中的影像覆疊
每個影像清單 ([CImageList](../mfc/reference/cimagelist-class.md)) 包含用於覆疊遮罩的影像清單。 「覆疊遮罩」是一個以透明方式繪製在另一個影像上的影像。 所有影像都可以當做覆疊遮罩。 您最多可以為每個影像清單指定四個覆疊遮罩。  
  
 使用覆疊遮罩的清單新增影像索引[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)成員函式、 影像、 索引和覆疊遮罩的索引。 請注意，覆疊遮罩的索引是以一起始而不是以零起始。  
  
 您透過使用單一呼叫影像繪製覆疊遮罩**繪製**。 其中的參數包含影像的索引和繪製覆疊遮罩的索引。 您必須使用[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)巨集來指定覆疊遮罩的索引。 您也可以指定覆疊影像，當呼叫[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)成員函式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

