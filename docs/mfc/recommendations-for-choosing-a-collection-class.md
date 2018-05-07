---
title: 選擇集合類別的建議 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28527f9668b9ca6a9ef00cf399a04ce9bad65716
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="recommendations-for-choosing-a-collection-class"></a>選擇集合類別的建議
本文所包含的詳細資訊，旨在協助您選擇特定應用程式所需的集合類別。  
  
 集合類別的選擇取決於許多因素，包括︰  
  
-   類別圖形的功能︰排序、編製索引和效能，如本主題稍後的 [集合圖形功能](#_core_collection_shape_features) 表格所示  
  
-   類別會使用 C++ 樣板與否  
  
-   儲存在集合中的項目是否可序列化  
  
-   儲存在集合中的項目是否可傾印以進行診斷  
  
-   集合是否為安全類型  
  
 以下的 [集合圖形功能](#_core_collection_shape_features)表格摘要說明可用集合圖形的特性。  
  
-   欄 2 和 3 描述每個圖形的排序和存取特性。 在下表中，「已排序」一詞是指項目的插入和刪除順序決定其在集合中的順序；而不是指項目依其內容排序。 「已編製索引」一詞是指集合中的項目可由整數索引擷取，就像是一般陣列中的項目。  
  
-   欄 4 和 5 描述每個圖形的效能。 在需要多次插入集合的應用程式中，插入速度可能特別重要；至於其他應用程式，查閱速度可能比較重要。  
  
-   欄 6 描述每個圖形是否允許重複的項目。  
  
### <a name="_core_collection_shape_features"></a>  集合圖形功能  
  
|圖形|排序|編製索引|插入項目|搜尋指定的項目|重複的項目|  
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|  
|清單|[是]|否|快速|緩慢|[是]|  
|陣列|[是]|依 int|緩慢|緩慢|[是]|  
|對應|否|依索引鍵|快速|快速|否 (索引鍵) 是 (值)|  
  
 以下的 [MFC 集合類別的特性](#_core_characteristics_of_mfc_collection_classes)表格摘要說明特定 MFC 集合類別的其他重要特性，可作為選擇時的指南。 您的選擇可能取決於下列因素：類別是否依據 C++ 範本、其元素是否可透過 MFC 的文件 [序列化](../mfc/serialization-in-mfc.md) 機制進行序列化、其元素是否可透過 MFC 的診斷傾印機制進行傾印，或者類別是否為型別安全 (換句話說，您是否可以保證元素的類型儲存在以類別為基礎的集合中，並從中擷取)。  
  
### <a name="_core_characteristics_of_mfc_collection_classes"></a>  MFC 集合類別的特性  
  
|類別|使用 C++<br /><br /> 範本|可以是<br /><br /> 已序列化|可以是<br /><br /> 已傾印|為<br /><br /> Type-Safe - 類型安全|  
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|  
|`CArray`|[是]|是 1|是 1|否|  
|`CByteArray`|否|是|[是]|是 3|  
|`CDWordArray`|否|是|[是]|是 3|  
|`CList`|[是]|是 1|是 1|否|  
|`CMap`|[是]|是 1|是 1|否|  
|`CMapPtrToPtr`|否|否|是|否|  
|`CMapPtrToWord`|否|否|是|否|  
|`CMapStringToOb`|否|是|是|否|  
|`CMapStringToPtr`|否|否|是|否|  
|`CMapStringToString`|否|是|[是]|是 3|  
|`CMapWordToOb`|否|是|是|否|  
|`CMapWordToPtr`|否|否|是|否|  
|`CObArray`|否|是|是|否|  
|`CObList`|否|是|是|否|  
|`CPtrArray`|否|否|是|否|  
|`CPtrList`|否|否|是|否|  
|`CStringArray`|否|是|[是]|是 3|  
|`CStringList`|否|是|[是]|是 3|  
|`CTypedPtrArray`|[是]|不一定 2|[是]|是|  
|`CTypedPtrList`|[是]|不一定 2|[是]|是|  
|`CTypedPtrMap`|[是]|不一定 2|[是]|是|  
|`CUIntArray`|否|否|[是]|是 3|  
|`CWordArray`|否|是|[是]|是 3|  
  
 1. 若要序列化，您必須明確呼叫集合物件的`Serialize`函式; 若要傾印，您必須明確呼叫其`Dump`函式。 您不能使用 `ar << collObj` 格式進行序列化，也不能使用 `dmp` `<< collObj` 格式進行傾印。  
  
 2. 能否序列化取決於基礎集合類型。 例如，如果具類型的指標陣列是以 `CObArray`為基礎，則可以序列化；如果是以 `CPtrArray`為基礎，則無法序列化。 一般而言，您無法序列化 "Ptr" 類別。  
  
 3. 如果在此欄中標示為 [是]，則非範本集合類別為型別安全 (但前提是您必須如預期般使用它)。 例如，如果您將位元組儲存在 `CByteArray`中，則陣列為型別安全。 但是，如果您用來儲存字元，就不一定是型別安全。  
  
## <a name="see-also"></a>另請參閱  
 [集合](../mfc/collections.md)   
 [樣板架構類別](../mfc/template-based-classes.md)   
 [如何： 建立類型安全集合](../mfc/how-to-make-a-type-safe-collection.md)   
 [存取集合的所有成員](../mfc/accessing-all-members-of-a-collection.md)

