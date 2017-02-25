---
title: "bitset 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bitset/std::bitset"
  - "std::bitset"
  - "std.bitset"
  - "bitset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitset 類別"
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# bitset 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述物件類型，其可儲存由固定位元數所組成的序列，以提供精簡的方式，來保留一組項目或條件的旗標。  bitset 類別支援類型 bitset 物件上的作業，該作業包含位元的集合，並提供每一個位元的常數時間存取。  
  
## 語法  
  
```  
  
     template <size_t   
     N  
     >  
class bitset  
```  
  
#### 參數  
 *N*  
 指定 bitset 物件中的位元數，搭配非零整數的類型 **size\_t**，其在編譯時期必須為已知 。  
  
## 備註  
 不同於類似的 [vector\<bool\> 類別](../standard-library/vector-bool-class.md)，bitset 類別並沒有迭代器，而且不是標準範本程式庫容器。  它也與 vector\<bool\> 在編譯時期固定的指定大小相異，與範本參數 **N** 在 **bitset \<N\>** 宣告時指定的大小一致。  
  
 如果位元值為 1 則設定位元，如果其值為 0 則重設。  若要翻轉或切換位元，方法是從 1 到 0 或從 0 到 1 變更其值。  bitset 中的 **N** 位元會由從 0 到 **N** \- 1 的整數值編製索引，其中 0 為第一個位元位置的索引，**N**\- 1 是最終位元位置。  
  
### 建構函式  
  
|||  
|-|-|  
|[bitset](../Topic/bitset::bitset.md)|建構 `bitset<N>` 類別的物件並將此位元初始化為零、某指定值或字串字元中取得的值。|  
  
### Typedef  
  
|||  
|-|-|  
|[element\_type](../Topic/bitset::element_type.md)|資料類型 `bool` 同義字的類型，可以用來參考 `bitset` 中的項目位元。|  
  
### 成員函式  
  
|||  
|-|-|  
|[全部](../Topic/bitset::all.md)|測試這個 `bitset` 中的所有位元，以判斷是否全部設定為 `true`。|  
|[任何](../Topic/bitset::any.md)|此成員函式會測試該序列中的任何位元是否設為 1。|  
|[count](../Topic/bitset::count.md)|此成員函式會傳回位元序列中設定的位元數。|  
|[flip](../Topic/bitset::flip.md)|切換 `bitset` 中的所有位元值，或在指定位置切換單一位元。|  
|[無](../Topic/bitset::none.md)|測試在 `bitset` 物件中是否沒有已設為 1 的位元。|  
|[重設](../Topic/bitset::reset.md)|將 `bitset` 中的所有位元重設為 0，或將指定位置的位元重設為 0。|  
|[設定](../Topic/bitset::set.md)|將 `bitset` 中的所有位元設為 1，或將指定位置的位元設為 1。|  
|[大小](../Topic/bitset::size.md)|傳回 `bitset` 物件中的位元數。|  
|[測試](../Topic/bitset::test.md)|測試位於 `bitset` 中指定位置的位元是否設為 1。|  
|[to\_string](../Topic/bitset::to_string.md)|將 `bitset` 物件轉換為字串表示。|  
|[to\_ullong](../Topic/bitset::to_ullong.md)|以 `unsigned long long` 傳回 `bitset` 中的位元值總和。|  
|[to\_ulong](../Topic/bitset::to_ulong.md)|將 `bitset` 物件轉換成 `unsigned long`，如果用來初始化 `bitset`，其可能產生所包含位元的序列。|  
  
### 成員類別  
  
|||  
|-|-|  
|[參考](../Topic/bitset::reference.md)|Proxy 類別，提供參考給包含於 `bitset` 中的位元，而 bitset 是用來存取及管理做為類別 `bitset` 之 `operator[]` 協助程式類別的個別位元。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/bitset::operator!=.md)|測試目標 `bitset` 是否與指定的 `bitset` 不相等。|  
|[operator&\=](../Topic/bitset::operator&=.md)|以邏輯 `AND` 作業執行 bitset 的位元組合。|  
|[運算子 \<\<](../Topic/bitset::operator%3C%3C.md)|以位置的指定數目將 `bitset` 中的位元移位至左邊，並傳回結果至新的 `bitset`。|  
|[operator\<\<\=](../Topic/bitset::operator%3C%3C=.md)|以位置的指定數目將 `bitset` 中的位元移位至左邊，並傳回結果至目標的 `bitset`。|  
|[operator\=\=](../Topic/bitset::operator==.md)|測試目標 `bitset` 是否與指定之 `bitset` 相等。|  
|[運算子 \>\>](../Topic/bitset::operator%3E%3E.md)|以位置的指定數目將 `bitset` 中的位元移位至右邊，並傳回結果至新的 `bitset`。|  
|[operator\>\>\=](../Topic/bitset::operator%3E%3E=.md)|以位置的指定數目將 `bitset` 中的位元移位至右邊，並傳回結果至目標的 `bitset`。|  
|[operator&#91;&#93;](../Topic/bitset::operator.md)|如果 `bitset` 可修改，則傳回位於 `bitset` 中指定位置的位元參考；否則它會傳回該位置的位元值。|  
|[operator^\=](../Topic/bitset::operator%5E=.md)|以互斥 `OR` 作業執行 bitset 的位元組合。|  
|[operator&#124;\=](../Topic/bitset::operator%7C=.md)|以包含 `OR` 作業執行 bitset 的位元組合。|  
|[operator~](../Topic/bitset::operator~.md)|切換 `bitset` 目標中的所有位元，並傳回結果。|  
  
## 需求  
 **標頭：**\<bitset\>  
  
 **命名空間:** std