---
title: 影像的影像清單中的資訊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b45a685a9de44bdc40f83481cb83ef58a5c4234
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343709"
---
# <a name="image-information-in-image-lists"></a>影像清單中的影像資訊
[CImageList](../mfc/reference/cimagelist-class.md)包含數個會擷取影像清單中的資訊函式。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成員函式會填滿`IMAGEINFO`包含影像和遮罩點陣圖的色彩平面和每像素的位元數目及周框的控制代碼的單一映像的相關資訊的結構影像點陣圖內影像。 您可以使用此項資訊直接操作影像的點陣圖。  
  
 [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成員函式會擷取影像清單中的影像數目。  
  
 您可以建立圖示的影像和遮罩影像清單中的使用根據[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成員函式。 函式會傳回新圖示的控制代碼。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

