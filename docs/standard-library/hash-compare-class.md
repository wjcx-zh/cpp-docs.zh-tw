---
title: "hash_compare 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hash_set/stdext::hash_compare"
  - "std.hash_compare"
  - "hash_compare"
  - "std::hash_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_compare 類別"
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# hash_compare 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此範本類別描述的物件，可由任一雜湊相關聯的容器 \(hash\_map、hash\_multimap、hash\_set 或 hash\_multiset\) 當成預設 **Traits** 參數物件使用，以便排序與雜湊處理所包含的項目。  
  
## 語法  
  
```  
template<class Key, class Traits = less<Key> >  
   class hash_compare  
   {  
   Traits comp;  
public:  
   const size_t bucket_size = 4;  
   const size_t min_buckets = 8;  
   hash_compare( );  
   hash_compare( Traits pred );  
   size_t operator( )( const Key& _Key ) const;  
   bool operator( )(   
      const Key& _Key1,  
      const Key& _Key2  
   ) const;  
   };  
```  
  
## 備註  
 每個雜湊相關聯的容器都會儲存 **Traits** 類型 \(範本參數\) 的雜湊特性物件。  您可以選擇性地覆寫特定函式與物件，從特製的 hash\_compare 衍生類別，或如果您符合特定的基本需求，則可以提供您自己這個類別的版本。  尤其是針對類型 **hash\_compare\<Key, Traits\>** 的 hash\_comp 物件，上述容器需要下列行為：  
  
-   為 **Key** 類型的所有 `_Key` 值，呼叫 **hash\_comp**\(`_Key`\) 做為雜湊函式，如此可產生 **size\_t** 類型值的分佈。  hash\_compare 所提供的函式會傳回 `_Key`。  
  
-   針對序列中具有相同雜湊值 \(雜湊函式傳回的值\) 且位於 `_Key2` 之前的所有 **Key** 類型之 `_Key1` 值，**hash\_comp**\(`_Key2`, `_Key1`\) 為 false。  函式必須加上 **Key** 類型值的總計排序。  hash\_compare 所提供的函式，會傳回 *comp*\(`_Key2`、`_Key1`\)`,`，其中 *comp* 是 **Traits** 類型的預存物件，您可以在建構 hash\_comp 物件時指定此物件。  預設的 **Traits** 參數類型 **less\<Key\>**，永遠不會減少值中的排序鍵。  
  
-   整數常數 **bucket\_size** 可指定容器在每個「值區」\(雜湊資料表項目\) 中不應超過的平均項目數。  此數目必須大於零。  hash\_compare 所提供的值為 4。  
  
-   整數常數 **min\_buckets** 可指定雜湊資料表中維護的最小值區數。  此數目必須是二次方且大於零。  hash\_compare 所提供的值為 8。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間。  如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
## 範例  
 請參閱 [hash\_map:: hash\_map](../Topic/hash_map::hash_map.md)、[hash\_multimap:: hash\_multimap](../Topic/hash_multimap::hash_multimap.md)、[hash\_set:: hash\_set](../Topic/hash_set::hash_set.md) 和 [hash\_multiset:: hash\_multiset](../Topic/hash_multiset::hash_multiset.md) 的範例，同時可參閱如何宣告及使用 hash\_compare 的範例。  
  
## 需求  
 **標頭：**\<hash\_map\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)