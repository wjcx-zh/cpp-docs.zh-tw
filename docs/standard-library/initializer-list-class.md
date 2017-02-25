---
title: "initializer_list Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# initializer_list Class
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供對項目的陣列之存取，其中每個成員都有指定的類型。  
  
## 語法  
  
```cpp  
template<  
    class Type >  
    class initializer_list  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`_Elem`|要存放在 `initializer_list` 中的項目資料類型。|  
|`_First`|指向 `initializer_list` 第一個項目的指標。|  
|`_Last`|指向 `initializer_list` 最後一個項目的指標。|  
  
## 備註  
 可以使用括號初始設定式清單建構 `initializer_list`：  
  
```cpp  
initializer_list<int> i1{ 1, 2, 3, 4 };  
```  
  
 每當函式簽章需要 `initializer_list` 時，編譯器會將以大括號括住且具有同質項目的初始設定式清單轉換至 `initializer_list`。  如需使用 `initializer_list` 的詳細資訊，請參閱[統一初始設定和委派建構函式](../cpp/uniform-initialization-and-delegating-constructors.md)。  
  
### 建構函式  
  
|||  
|-|-|  
|[initializer\_list](../Topic/forward_list::forward_list.md)|建構 `initializer_list` 類型的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|value\_type|`initializer_list` 中的項目類型。|  
|參考|類型，提供在 `initializer_list` 中之項目的參考。|  
|const\_reference|類型，提供在 `initializer_list` 中之項目的常數參考。|  
|size\_type|代表 `initializer_list` 中項目數的類型。|  
|迭代器|提供 `initializer_list` 之迭代器的類型。|  
|const\_iterator|提供 `initializer_list` 之常數迭代器的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[begin](../Topic/initializer_list::begin.md)|傳回 `initializer_list` 中第一個項目的指標。|  
|[end](../Topic/initializer_list::end.md)|傳回超出 `initializer_list` 中最後一個項目的項目指標。|  
|[大小](../Topic/initializer_list::size.md)|傳回 `initializer_list` 中項目的數目。|  
  
## 需求  
 **標頭：**\<initializer\_list\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<forward\_list\>](../standard-library/forward-list.md)