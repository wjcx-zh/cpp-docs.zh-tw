---
title: 存取集合的所有成員 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec9757a463bce7ef873720f229b70da695deae8d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-all-members-of-a-collection"></a>存取集合的所有成員
MFC 陣列集合類別 (範本型和非範本型) 使用索引來存取其項目。 MFC 清單和對應集合類別 (範本型和非範本型) 使用 **POSITION** 類型的指標來描述集合中的指定位置。 若要存取這些集合的一或多個成員，請先將位置指標初始化，然後將該位置重複傳遞給集合，並要求它傳回下一個項目。 集合不負責維護反覆項目進度的相關狀態資訊。 該資訊會保留在位置指示器中。 但若指定特定位置，集合會負責傳回下一個元素。  
  
 下列程序示範如何逐一查看隨 MFC 提供的三種主要集合類型︰  
  
-   [逐一查看陣列](#_core_to_iterate_an_array)  
  
-   [逐一查看清單](#_core_to_iterate_a_list)  
  
-   [逐一查看對應](#_core_to_iterate_a_map)  
  
### <a name="_core_to_iterate_an_array"></a> 逐一查看陣列  
  
1.  使用循序索引編號並搭配 `GetAt` 成員函式︰  
  
     [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]  
  
     此範例使用具類型的指標陣列，其中包含 `CPerson` 物件的指標。 此陣列衍生自類別 `CObArray`，這是其中一個預先定義的非範本類別。 `GetAt` 傳回 `CPerson` 物件的指標。 針對具類型的指標集合類別 (陣列或清單)，第一個參數會指定基底類別，第二個參數會指定要儲存的類型。  
  
     `CTypedPtrArray`類別也會多載 **[]** 運算子，讓您可以使用慣用的陣列註標語法來存取元素的陣列。 上述 `for` 迴圈主體中的陳述式可替代成  
  
     [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]  
  
     **const** 和非**const** 版本中都有此運算子。 針對 **const** 陣列叫用的 **const** 版本，只能出現在指派陳述式的右邊。  
  
### <a name="_core_to_iterate_a_list"></a> 逐一查看清單  
  
1.  使用成員函式 `GetHeadPosition` 和 `GetNext` 來執行清單︰  
  
     [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]  
  
     此範例使用具類型的指標清單來包含 `CPerson` 物件的指標。 此清單宣告類似於 [逐一查看陣列](#_core_to_iterate_an_array) 程序中對陣列所做的宣告，但衍生自類別 `CObList`。 `GetNext` 傳回 `CPerson` 物件的指標。  
  
### <a name="_core_to_iterate_a_map"></a> 逐一查看對應  
  
1.  使用 `GetStartPosition` 移至對應的開頭，並使用 `GetNextAssoc` 重複取得對應中的下一組索引鍵和值，如下列範例所示︰  
  
     [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]  
  
     此範例使用簡單的對應範本 (而不是具類型的指標集合)，該範本使用 `CString` 索引鍵，並將指標儲存至 `CPerson` 物件。 當您使用 `GetNextAssoc`等存取函式時，該類別會提供 `CPerson` 物件的指標。 如果您改用其中一個非範本對應集合，您必須將傳回的 `CObject` 指標轉換成 `CPerson`的指標。  
  
    > [!NOTE]
    >  若是非範本對應，編譯器需要參考傳遞給 `CObject` 之最後一個參數中的 `GetNextAssoc`指標。 輸入時，您必須將指標轉換成該類型，如下一個範例所示。  
  
     此範本解決方案比較簡單，並可協助改善型別安全。 非範本程式碼則比較複雜，如下所示︰  
  
     [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]  
  
 如需詳細資訊，請參閱 [刪除 CObject 集合中的所有物件](../mfc/deleting-all-objects-in-a-cobject-collection.md)。  
  
## <a name="see-also"></a>另請參閱  
 [集合](../mfc/collections.md)

