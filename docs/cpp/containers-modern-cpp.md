---
title: "容器 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，使用 [向量](../standard-library/vector-class.md) c + + 中的預設循序容器。 這相當於清單的 \< T> 以其他語言。  
  
```cpp  
vector<string> v;  
v.push_back( "Geddy Lee" );  
  
```  
  
 使用 [對應](../standard-library/map-class.md) (不 unordered_map) 做為預設的關聯容器。 使用 [設定](../standard-library/set-class.md), ，[multimap](../standard-library/multimap-class.md), ，[multiset](../standard-library/multiset-class.md) 變質與多個案例。  
  
```cpp  
map<string, string> phone_book;  
// ...  
phone_book["Alex Lifeson"] = "+1 (416) 555-1212";  
  
```  
  
 當需要效能最佳化時，請考慮使用︰  
  
1.  內嵌陣列型別是很重要-例如，做為成員。  
  
2.  未排序的關聯容器 (unordered_map 等等)：較低的每個項目額外負荷 (主要) 和固定時間搜尋 (可能是主要，有時候為次要)。 難以正確且有效率地使用，因為使用不便且邊緣銳利。  
  
3.  排序的向量。 (請參閱︰ [演算法](../cpp/algorithms-modern-cpp.md)。)  
  
 不使用 C 陣列。 (對於較舊的 Api，使用 `f( vec.data(), vec.size() );` 。)  
  
 如需容器另一篇文章，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
## <a name="container-sizes"></a>容器的大小  
 下表顯示的容器大小，以位元組為單位，適用於 x86 和 x64 平台。  （針對這些用途，32 位元 ARM 就相當於 x86。）這些資料表包含發行模式中，因為偵錯模式包含檢查機制來使用空間和時間。  個別的資料行對於 [!INCLUDE[cpp_orcas_long](../cpp/includes/cpp_orcas_long_md.md)] SP1，其中 `_SECURE_SCL` 預設為 1，至於 [!INCLUDE[cpp_orcas_long](../cpp/includes/cpp_orcas_long_md.md)] SP1 `_SECURE_SCL` 手動設定為 0，最快的速度。  在 Visual Studio 2010 中，visual c + + [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], ，和 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 預設 `_SECURE_SCL` 設為 0 (現在稱為 `_ITERATOR_DEBUG_LEVEL`)。  
  
|x86 容器大小 （位元組）|VC9 SP1|VC9 SP1<br /><br /> SCL=0|VC10|VC11|  
|-----------------------------------|-------------|------------------------|----------|----------|  
|向量 \< int>|24|16|16|12|  
|陣列 \< int、 5 >|20|20|20|20|  
|deque \< int>|32|32|24|20|  
|forward_list \< int>|N/A|N/A|8|4|  
|清單 \< int>|28|12|12|8|  
|priority_queue \< int>|28|20|20|16|  
|佇列 \< int>|32|32|24|20|  
|堆疊 \< int>|32|32|24|20|  
|對 \< int、 int >|8|8|8|8|  
|tuple \< int、 int、 int >|16|16|16|12|  
|地圖 \< int、 int >|32|12|16|8|  
|多重對應 \< int、 int >|32|12|16|8|  
|設定 \< int>|32|12|16|8|  
|多重集 \< int>|32|12|16|8|  
|hash_map \< int、 int >|72|44|44|32|  
|hash_multimap \< int、 int >|72|44|44|32|  
|hash_set \< int>|72|44|44|32|  
|hash_multiset \< int>|72|44|44|32|  
|unordered_map \< int、 int >|72|44|44|32|  
|unordered_multimap \< int、 int >|72|44|44|32|  
|unordered_set \< int>|72|44|44|32|  
ordered_multiset \< int>|72|44|44|32|  
|string|28|28|28|24|  
|wstring|28|28|28|24|  
  
|x64 容器大小 （位元組）|VC9 SP1|VC9 SP1<br /><br /> SCL=0|VC10|VC11|  
|-----------------------------------|-------------|------------------------|----------|----------|  
|向量 \< int>|48|32|32|24|  
|陣列 \< int、 5 >|20|20|20|20|  
|deque \< int>|64|64|48|40|  
|forward_list \< int>|N/A|N/A|16|8|  
|清單 \< int>|56|24|24|16|  
|priority_queue \< int>|56|40|40|32|  
|佇列 \< int>|64|64|48|40|  
|堆疊 \< int>|64|64|48|40|  
|對 \< int、 int >|8|8|8|8|  
|tuple \< int、 int、 int >|16|16|16|12|  
|地圖 \< int、 int >|64|24|32|16|  
|多重對應 \< int、 int >|64|24|32|16|  
|設定 \< int>|64|24|32|16|  
|多重集 \< int>|64|24|32|16|  
|hash_map \< int、 int >|144|88|88|64|  
|hash_multimap \< int、 int >|144|88|88|64|  
|hash_set \< int>|144|88|88|64|  
|hash_multiset \< int>|144|88|88|64|  
|unordered_map \< int、 int >|144|88|88|64|  
|unordered_multimap \< int、 int >|144|88|88|64|  
|unordered_set \< int>|144|88|88|64|  
ordered_multiset \< int>|144|88|88|64|  
|string|40|40|40|32|  
|wstring|40|40|40|32|  
  
## <a name="see-also"></a>另請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)