---
title: 使用影像清單 |Microsoft 文件
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
ms.openlocfilehash: 5722a2ef8c4e93e4996ee243b3c01b6dd6aeca78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-image-list"></a>使用影像清單
影像清單的一般使用方式會遵循下列模式：  
  
-   建構[CImageList](../mfc/reference/cimagelist-class.md)物件，並呼叫其中一個多載其[建立](../mfc/reference/cimagelist-class.md#create)函式來建立影像清單，並將其附加至`CImageList`物件。  
  
-   如果您未將影像加入您在建立映像清單時，將影像加入至映像清單藉由呼叫[新增](../mfc/reference/cimagelist-class.md#add)或[讀取](../mfc/reference/cimagelist-class.md#read)成員函式。  
  
-   呼叫適當的成員函式，該控制項與控制項相關聯的影像清單或繪製影像的影像清單中使用影像清單的自行[繪製](../mfc/reference/cimagelist-class.md#draw)成員函式。  
  
-   可能是可讓使用者拖曳影像，使用的拖曳影像清單的內建支援。  
  
> [!NOTE]
>  如果使用影像清單建立**新**運算子，您必須終結`CImageList`物件與它完成時。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

