---
title: "管理影像清單 |Microsoft 文件"
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
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c2670f3935e2f4c482728000a268cb46cc9dbdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="manipulating-image-lists"></a>管理影像清單
[取代](../mfc/reference/cimagelist-class.md#replace)成員函式取代影像清單中的映像 ([CImageList](../mfc/reference/cimagelist-class.md)) 與新的映像。 如果需要動態增加影像清單物件中的影像數目，此函式也很有用。 [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount)函式會動態變更影像清單中所儲存的影像數目。 如果您增加影像清單的大小，請呼叫**取代**將影像加入至新的映像位置。 如果您縮小影像清單的大小，則會釋放超出新的大小之外的影像。  
  
 [移除](../mfc/reference/cimagelist-class.md#remove)成員函式會移除從影像清單的映像。 [複製](../mfc/reference/cimagelist-class.md#copy)成員函式可以複製或交換影像清單內的影像。 此函式可讓您指出來源影像應該複製到目的地索引，還是應該交換來源和目的地影像。  
  
 若要建立新的映像清單合併兩個映像清單，請使用 的適當多載[建立](../mfc/reference/cimagelist-class.md#create)成員函式。 這個多載**建立**合併現有的映像的第一個影像清單，將產生的影像儲存在新的影像清單物件。 新的影像會以在第一個影像上繪製透明的第二個影像來立。 新影像的遮罩是在兩個現有影像的遮罩位元上執行邏輯 OR 運算的結果。  
  
 這會一直重複直到所有影像都合併和加入新的影像清單物件為止。  
  
 您可以將影像資訊寫入封存藉由呼叫[寫入](../mfc/reference/cimagelist-class.md#write)成員函式，以及其讀回呼叫[讀取](../mfc/reference/cimagelist-class.md#read)成員函式。  
  
 [GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle)，[附加](../mfc/reference/cimagelist-class.md#attach)，和[卸離](../mfc/reference/cimagelist-class.md#detach)成員函式可讓您操作附加至影像清單控制代碼`CImageList`物件時[DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist)成員函式會刪除影像清單，而不會終結`CImageList`物件。  
  
## <a name="see-also"></a>請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

