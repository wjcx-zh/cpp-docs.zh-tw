---
title: "hash_compare 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_set/stdext::hash_compare
- hash_compare
dev_langs:
- C++
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 56b02a7bcafebebfb9fbb5569ad28eb2d52cf879
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="hashcompare-class"></a>hash_compare 類別
此範本類別描述的物件可供任一雜湊關聯容器 (hash_map、hash_multimap、hash_set 或 hash_multiset) 作為預設 **Traits** 參數物件，用來排序及雜湊處理它們所包含的元素。  
  
## <a name="syntax"></a>語法  
  
class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };  
  
## <a name="remarks"></a>備註  
 每個雜湊關聯容器都會儲存 **Traits** 類型 (範本參數) 的雜湊特性物件。 您可以選擇性地覆寫特定函式與物件，從特製的 hash_compare 衍生類別，或如果您符合特定的基本需求，則可以提供您自己這個類別的版本。 更明確地說，針對 **hash_compare\<Key, Traits>** 類型的 hash_comp 物件，上述容器必須要有下列行為：  
  
-   針對 **Key** 類型的所有 `key` 值，**hash_comp**( `key`) 呼叫會作為雜湊函式，這會產生 **size_t** 類型值的分佈。 hash_compare 所提供的函式會傳回 `key`。  
  
-   針對序列中位於 `key2` 之前且具有相同雜湊值 (雜湊函式所傳回的值) 之任何 **Key** 類型的 `key1` 值，**hash_comp**( `key2`, `key1`) 會是 false。 函式必須在 **Key** 類型的值上強制加上總排序。 hash_compare 所提供的函式會傳回 *comp*( `key2`, `key1`) `,`，其中 *comp* 是 **Traits** 類型的預存物件，您可以在建構 hash_comp 物件時指定此物件。 針對預設的 **Traits** 參數類型 **less\<Key>**，排序鍵的值一律不會縮減。  
  
-   整數常數 **bucket_size** 可指定容器在每個「值區」(雜湊資料表項目) 中不應超過的平均元素數目。 此數目必須大於零。 hash_compare 所提供的值為 4。  
  
-   整數常數 **min_buckets** 可指定雜湊資料表中要維護的值區數目下限。 此數目必須是二次方且大於零。 hash_compare 所提供的值為 8。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
## <a name="example"></a>範例  
 如需如何宣告及使用 hash_compare 的範例，請參閱 [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map)、[hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap)、[hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) 及 [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) 的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<hash_map>  
  
 **命名空間：** stdext  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




