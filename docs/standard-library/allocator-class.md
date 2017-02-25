---
title: "allocator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::allocator"
  - "allocator"
  - "memory/std::allocator"
  - "std.allocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator 類別"
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# allocator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述物件，該物件管理 **Type** 類型物件陣列的儲存空間配置和釋放。**allocator** 類別的物件是建構函式中指定的預設配置器物件，為針對 Standard C\+\+ 程式庫中的數個容器樣板類別所指定。  
  
## 語法  
  
```  
  
template <class   
Type  
>  
class allocator  
  
```  
  
#### 參數  
 *類型*  
 正在配置或取消配置儲存體的物件類型。  
  
## 備註  
 所有標準樣板程式庫容器都具有樣板參數，預設值為 **allocator**。 建構包含自訂配置器的容器可控制該容器之項目的配置與釋放。  
  
 例如，配置器物件可在私密堆積或共用記憶體中配置儲存體，或是可針對小型或大型物件最佳化。 它也能指定透過其提供的類型定義，透過管理共用記憶體的特殊存取子物件來存取項目，或是執行自動化記憶體回收。 因此，使用配置器物件來配置儲存區的類別，應該使用這些類型來宣告指標和參考物件，如 Standard C\+\+ 程式庫中的容器所做的一般。  
  
 **\(僅限 C\_\+\+98\/03\)**從 allocator 類別衍生時，您必須提供 [rebind](../Topic/allocator::rebind.md) 結構，其 `_Other` typedef 會參考您最近衍生的類別。  
  
 因此，配置器會定義下列類型：  
  
-   [pointer](../Topic/allocator::pointer.md) 行為類似於 \[**類型**\] 指標。  
  
-   [const\_pointer](../Topic/allocator::const_pointer.md) 行為類似於 \[**類型**\] 的 const 指標。  
  
-   [reference](../Topic/allocator::reference.md) 行為類似於 \[**類型**\] 的參考。  
  
-   [const\_reference](../Topic/allocator::const_reference.md) 行為類似於 \[**類型**\] 的 const 參考。  
  
 這些 \[**類型**\] 會指定指標和參考必須為配置的項目所採用的格式。 \([allocator:: pointer](../Topic/allocator::pointer.md) 不一定與所有配置器的 \[**類型**\]\* 相同，即使它針對 **allocator** 類別明顯定義此類型也是如此。\)  
  
 **C \+ \+ 11 和更新版本：**若要在您的配置器中啟用移動運算，請使用最小的配置器介面與實作複製建構函式、\=\= 和 \!\= 運算子、配置及取消配置。 如需詳細資訊和範例，請參閱[配置器](../standard-library/allocators.md)。  
  
## Members  
  
### 建構函式  
  
|||  
|-|-|  
|[allocator](../Topic/allocator::allocator.md)|建構函式可用來建立 `allocator` 物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[const\_pointer](../Topic/allocator::const_pointer.md)|一種類型，可提供配置器管理之物件類型的常數指標。|  
|[const\_reference](../Topic/allocator::const_reference.md)|一種類型，可提供配置器管理之物件類型的常數參考。|  
|[difference\_type](../Topic/allocator::difference_type.md)|帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。|  
|[指標](../Topic/allocator::pointer.md)|一種類型，可提供配置器管理之物件類型的指標。|  
|[參考](../Topic/allocator::reference.md)|一種類型，可提供配置器管理之物件類型的參考。|  
|[size\_type](../Topic/allocator::size_type.md)|不帶正負號的整數類型，可以代表樣板類別 `allocator` 的物件可配置的任何序列的長度。|  
|[value\_type](../Topic/allocator::value_type.md)|配置器所管理的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[位址](../Topic/allocator::address.md)|尋找指定值所屬物件的位址。|  
|[allocate](../Topic/allocator::allocate.md)|配置夠大的記憶體區塊，至少儲存某些指定的項目數。|  
|[建構](../Topic/allocator::construct.md)|在指定值初始化的指定位址上，建構特定類型的物件。|  
|[取消配置](../Topic/allocator::deallocate.md)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[終結](../Topic/allocator::destroy.md)|呼叫物件解構函式，而不取消配置儲存物件的記憶體。|  
|[max\_size](../Topic/allocator::max_size.md)|傳回在可用記憶體用完之前，無法由類別 `allocator`的物件配置之類型 `Type` 的項目數量。|  
|[重新繫結](../Topic/allocator::rebind.md)|一種結構，可讓某個類型的物件配置器，為另一種類型的物件配置儲存體。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/allocator::operator=.md)|將一個 `allocator` 物件指派給另一個 `allocator` 物件。|  
  
## 需求  
 **標頭：**\<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)