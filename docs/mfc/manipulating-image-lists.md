---
title: 管理影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: cb7376241febd6bd1545cd183147e14a15313820
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622452"
---
# <a name="manipulating-image-lists"></a>管理影像清單

[Replace](reference/cimagelist-class.md#replace)成員函式會以新的影像取代影像清單（[CImageList](reference/cimagelist-class.md)）中的影像。 如果需要動態增加影像清單物件中的影像數目，此函式也很有用。 [SetImageCount](reference/cimagelist-class.md#setimagecount)函數會動態變更影像清單中儲存的影像數目。 如果您增加影像清單的大小，請呼叫 `Replace` 以將影像新增至新的影像位置。 如果您縮小影像清單的大小，則會釋放超出新的大小之外的影像。

[Remove](reference/cimagelist-class.md#remove)成員函式會移除影像清單中的影像。 [Copy](reference/cimagelist-class.md#copy)成員函式可以在影像清單中複製或交換影像。 此函式可讓您指出來源影像應該複製到目的地索引，還是應該交換來源和目的地影像。

若要藉由合併兩個影像清單來建立新的影像清單，請使用[create](reference/cimagelist-class.md#create)成員函式的適當多載。 這個多載會 `Create` 合併現有影像清單的第一個影像，並將產生的影像儲存在新的影像清單物件中。 新的影像會以在第一個影像上繪製透明的第二個影像來立。 新影像的遮罩是在兩個現有影像的遮罩位元上執行邏輯 OR 運算的結果。

這會一直重複直到所有影像都合併和加入新的影像清單物件為止。

您可以藉由呼叫[write](reference/cimagelist-class.md#write)成員函式，將影像資訊寫入封存，並藉由呼叫[read](reference/cimagelist-class.md#read)成員函式將它讀回。

[GetSafeHandle](reference/cimagelist-class.md#getsafehandle)、 [Attach](reference/cimagelist-class.md#attach)和[Detach](reference/cimagelist-class.md#detach)成員函式可讓您操作附加至物件之影像清單的控制碼 `CImageList` ，而[DeleteImageList](reference/cimagelist-class.md#deleteimagelist)成員函式則會刪除影像清單，而不會終結 `CImageList` 物件。

## <a name="see-also"></a>另請參閱

[使用 CImageList](using-cimagelist.md)<br/>
[控制項](controls-mfc.md)
