---
title: 刪除 CObject 集合中的所有物件
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 303b8a566a730c5abd06d51fb7977174e19a6435
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370543"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>刪除 CObject 集合中的所有物件

本文說明如何刪除集合中的所有物件 (不需刪除集合物件本身)。

要刪除`CObject`s 集合中的所有物件(或派`CObject`生自的物件),請使用「[存取集合的所有成員](../mfc/accessing-all-members-of-a-collection.md)」一文中描述的反覆運算技術之一依次刪除每個物件。

> [!CAUTION]
> 集合中的物件可以共用。 也就是，集合會中保留物件指標，而程式的其他部分可能也有到同一物件的指標。 您必須留意不要刪除共用的物件，直到所有部分都已用完物件。

本文說明如何刪除物件於：

- [清單](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [陣列](#_core_to_delete_all_elements_in_an_array)

- [對應](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>刪除 XObject 的指標清單中的所有物件

1. 使用 `GetHeadPosition` 和 `GetNext` 逐一查看清單。

1. 使用**delete**運算符刪除反覆運算中遇到的每個物件。

1. 在刪除與這些項目關聯的物件後，呼叫 `RemoveAll` 函式將所有項目從清單移除。

下列範例顯示如何從 `CPerson` 物件清單刪除所有物件。 清單中的每個物件，是堆積上最初配置之 `CPerson` 物件的指標。

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

最後一個函式呼叫 `RemoveAll`，是從清單移除所有項目的清單成員函式。 成員函式 `RemoveAt` 會移除單一項目。

請留意刪除項目的物件和移除項目本身之間的差異。 從清單移除項目只會移除對物件的參考。 物件仍然存在於記憶體中。 當您刪除物件時，它就不會存在，且其記憶體會被回收。 因此，在項目物件已刪除後立即移除項目是很重要的，如此清單才不會嘗試存取不存在的物件。

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>移除陣列中的所有元素

1. 使用 `GetSize` 和整數索引值以逐一查看陣列。

1. 使用**delete**運算符刪除反覆運算中遇到的每個元素。

1. 在刪除之後，呼叫 `RemoveAll` 函式以從陣列移除所有項目。

   用於刪除陣列中所有項目的程式碼如下所示：

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

如上述清單範例，您可以呼叫 `RemoveAll` 移除陣列中所有項目，或呼叫 `RemoveAt` 移除個別項目。

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>刪除地圖中的所有元素

1. 使用 `GetStartPosition` 和 `GetNextAssoc` 逐一查看陣列。

1. 使用**delete**運算符刪除反覆運算中遇到的每個映射元素的鍵和/或值。

1. 在刪除之後，呼叫 `RemoveAll` 函式以從對應移除所有項目。

   用於刪除 `CMap` 集合中所有項目的程式碼，如下所示。 對應中的每個項目都具有字串做為索引鍵，並以 `CPerson` 物件 (衍生自 `CObject`) 做為值。

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

您可以呼叫 `RemoveAll` 移除對應或 `RemoveKey` 的所有項目，以移除具有指定索引鍵的個別項目。

## <a name="see-also"></a>另請參閱

[存取集合的所有成員](../mfc/accessing-all-members-of-a-collection.md)
