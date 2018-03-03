---
title: "使用影像清單 |Microsoft 文件"
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
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4321649bf4e8fe0e34fef8fe37b8c96598bef2c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-image-list"></a>使用影像清單
影像清單的一般使用方式會遵循下列模式：  
  
-   建構[CImageList](../mfc/reference/cimagelist-class.md)物件，並呼叫其中一個多載其[建立](../mfc/reference/cimagelist-class.md#create)函式來建立影像清單，並將其附加至`CImageList`物件。  
  
-   如果您未將影像加入您在建立映像清單時，將影像加入至映像清單藉由呼叫[新增](../mfc/reference/cimagelist-class.md#add)或[讀取](../mfc/reference/cimagelist-class.md#read)成員函式。  
  
-   呼叫適當的成員函式，該控制項與控制項相關聯的影像清單或繪製影像的影像清單中使用影像清單的自行[繪製](../mfc/reference/cimagelist-class.md#draw)成員函式。  
  
-   可能是可讓使用者拖曳影像，使用的拖曳影像清單的內建支援。  
  
> [!NOTE]
>  如果使用影像清單建立**新**運算子，您必須終結`CImageList`物件與它完成時。  
  
## <a name="see-also"></a>請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

