---
title: "影像的影像清單中的資訊 |Microsoft 文件"
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
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33248c1bbc225d8d1ccf55c126d1657d0b0e4cad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="image-information-in-image-lists"></a>影像清單中的影像資訊
[CImageList](../mfc/reference/cimagelist-class.md)包含數個會擷取影像清單中的資訊函式。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成員函式會填滿`IMAGEINFO`包含影像和遮罩點陣圖的色彩平面和每像素的位元數目及周框的控制代碼的單一映像的相關資訊的結構影像點陣圖內影像。 您可以使用此項資訊直接操作影像的點陣圖。  
  
 [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成員函式會擷取影像清單中的影像數目。  
  
 您可以建立圖示的影像和遮罩影像清單中的使用根據[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成員函式。 函式會傳回新圖示的控制代碼。  
  
## <a name="see-also"></a>請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

