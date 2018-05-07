---
title: 清單項目和影像清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6bd7a97330a8a646a880bf229562dbec9a70181
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="list-items-and-image-lists"></a>清單項目和影像清單
清單控制項中的"item"([CListCtrl](../mfc/reference/clistctrl-class.md)) 圖示、 標籤和可能是其他資訊 （「 子項） 所組成。  
  
 清單控制項項目的圖示會出現在影像清單中。 影像清單包含圖示檢視中使用的完整大小圖示。 第二個 (選擇性) 影像清單包含與在控制項的其他檢視中使用相同圖示的較小版本。 第三個選擇性清單包含「狀態」影像 (例如核取方塊)，用於在某些檢視中顯示於小圖示的前方。 第四個選擇性清單包含一些在清單控制項的個別標頭項目中顯示的影像。  
  
> [!NOTE]
>  如果清單檢視控制項是使用 `LVS_SHAREIMAGELISTS` 樣式建立，您就要負責在不使用時終結影像清單。 如果您指派相同的影像清單給多個清單檢視控制項，請指定此樣式，否則可能出現多個控制項嘗試終結相同影像清單的情形。  
  
 如需清單項目，請參閱[清單檢視影像清單](http://msdn.microsoft.com/library/windows/desktop/bb774736)和[項目和子項目的](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。 另請參閱類別[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考*和[使用 CImageList](../mfc/using-cimagelist.md)此系列文章中。  
  
 若要建立清單控制項，您必須在插入新的項目至清單時，提供要使用的影像清單。 下列範例將說明此程序，其中 `m_pImagelist` 是 `CImageList` 類型的指標，而 `m_listctrl` 為 `CListCtrl` 資料成員。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 不過，如果您不打算在清單檢視或清單控制項中顯示圖示，則不需要影像清單。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

