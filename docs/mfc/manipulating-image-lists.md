---
title: 管理影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: 1e86961980c91ade47a3d6510dec5c04ac36cffb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304843"
---
# <a name="manipulating-image-lists"></a>管理影像清單

[取代](../mfc/reference/cimagelist-class.md#replace)成員函式會取代影像清單中的映像 ([CImageList](../mfc/reference/cimagelist-class.md)) 與新的映像。 如果需要動態增加影像清單物件中的影像數目，此函式也很有用。 [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount)函式會動態變更儲存在映像清單中的映像數目。 如果您增加影像清單的大小，呼叫`Replace`將影像新增至新的影像位置。 如果您縮小影像清單的大小，則會釋放超出新的大小之外的影像。

[移除](../mfc/reference/cimagelist-class.md#remove)成員函式會移除從影像清單的映像。 [複製](../mfc/reference/cimagelist-class.md#copy)成員函式可以複製或交換影像清單內的影像。 此函式可讓您指出來源影像應該複製到目的地索引，還是應該交換來源和目的地影像。

若要合併兩個映像清單，以建立新的映像清單，使用的適當多載[建立](../mfc/reference/cimagelist-class.md#create)成員函式。 這個多載`Create`列出現有的映像的第一個映像，將產生的影像儲存在新的影像清單物件的合併。 新的影像會以在第一個影像上繪製透明的第二個影像來立。 新影像的遮罩是在兩個現有影像的遮罩位元上執行邏輯 OR 運算的結果。

這會一直重複直到所有影像都合併和加入新的影像清單物件為止。

您可以將影像資訊寫入封存藉由呼叫[撰寫](../mfc/reference/cimagelist-class.md#write)成員函式，以及其讀回呼叫[讀取](../mfc/reference/cimagelist-class.md#read)成員函式。

[GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle)，[附加](../mfc/reference/cimagelist-class.md#attach)，並[卸離](../mfc/reference/cimagelist-class.md#detach)成員函式可讓您操作附加至影像清單的控制代碼`CImageList`物件，而[DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist)成員函式會刪除映像清單，而不會終結`CImageList`物件。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
