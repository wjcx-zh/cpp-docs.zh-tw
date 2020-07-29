---
title: 存取集合的所有成員
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
ms.openlocfilehash: cc058e6e4bf0058adb13f83e7ea071ebb4570ec4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214174"
---
# <a name="accessing-all-members-of-a-collection"></a>存取集合的所有成員

MFC 陣列集合類別 (範本型和非範本型) 使用索引來存取其項目。 MFC 清單和對應集合類別 (範本型和非範本型) 使用 **POSITION** 類型的指標來描述集合中的指定位置。 若要存取這些集合的一或多個成員，請先將位置指標初始化，然後將該位置重複傳遞給集合，並要求它傳回下一個項目。 集合不負責維護反覆項目進度的相關狀態資訊。 該資訊會保留在位置指示器中。 但若指定特定位置，集合會負責傳回下一個元素。

下列程序示範如何逐一查看隨 MFC 提供的三種主要集合類型︰

- [逐一查看陣列](#_core_to_iterate_an_array)

- [逐一查看清單](#_core_to_iterate_a_list)

- [逐一查看對應](#_core_to_iterate_a_map)

### <a name="to-iterate-an-array"></a><a name="_core_to_iterate_an_array"></a> 逐一查看陣列

1. 使用循序索引編號並搭配 `GetAt` 成員函式︰

   [!code-cpp[NVC_MFCCollections#12](codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]

   此範例使用具類型的指標陣列，其中包含 `CPerson` 物件的指標。 此陣列衍生自類別 `CObArray`，這是其中一個預先定義的非範本類別。 `GetAt` 傳回 `CPerson` 物件的指標。 針對具類型的指標集合類別 (陣列或清單)，第一個參數會指定基底類別，第二個參數會指定要儲存的類型。

   `CTypedPtrArray`類別也會多載 **[]** 運算子，讓您可以使用慣用的陣列注標語法來存取陣列的元素。 在上述迴圈主體中，語句的替代方法 **`for`** 是

   [!code-cpp[NVC_MFCCollections#13](codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]

   這個運算子同時存在於 **`const`** 和非 **`const`** 版本中。 針對陣列所叫用的版本，只能 **`const`** **`const`** 出現在指派語句的右側。

### <a name="to-iterate-a-list"></a><a name="_core_to_iterate_a_list"></a> 逐一查看清單

1. 使用成員函式 `GetHeadPosition` 和 `GetNext` 來執行清單︰

   [!code-cpp[NVC_MFCCollections#14](codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]

   此範例使用具類型的指標清單來包含 `CPerson` 物件的指標。 此清單宣告類似於 [逐一查看陣列](#_core_to_iterate_an_array) 程序中對陣列所做的宣告，但衍生自類別 `CObList`。 `GetNext` 傳回 `CPerson` 物件的指標。

### <a name="to-iterate-a-map"></a><a name="_core_to_iterate_a_map"></a> 逐一查看對應

1. 使用 `GetStartPosition` 移至對應的開頭，並使用 `GetNextAssoc` 重複取得對應中的下一組索引鍵和值，如下列範例所示︰

   [!code-cpp[NVC_MFCCollections#15](codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]

   此範例使用簡單的對應範本 (而不是具類型的指標集合)，該範本使用 `CString` 索引鍵，並將指標儲存至 `CPerson` 物件。 當您使用 `GetNextAssoc`等存取函式時，該類別會提供 `CPerson` 物件的指標。 如果您改用其中一個非範本對應集合，您必須將傳回的 `CObject` 指標轉換成 `CPerson`的指標。

    > [!NOTE]
    >  若是非範本對應，編譯器需要參考傳遞給 `CObject` 之最後一個參數中的 `GetNextAssoc`指標。 輸入時，您必須將指標轉換成該類型，如下一個範例所示。

   此範本解決方案比較簡單，並可協助改善型別安全。 非範本程式碼則比較複雜，如下所示︰

   [!code-cpp[NVC_MFCCollections#16](codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]

如需詳細資訊，請參閱 [刪除 CObject 集合中的所有物件](deleting-all-objects-in-a-cobject-collection.md)。

## <a name="see-also"></a>另請參閱

[集合](collections.md)
