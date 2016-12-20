---
title: "&lt;memory&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::<memory>"
  - "std.<memory>"
  - "<memory>"
  - "std::<memory>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memory 標頭"
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;memory&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義幫助配置和釋放物件的類別、運算子和數個範本。  
  
## 語法  
  
```  
  
#include <memory>  
  
```  
  
## 成員  
  
### 函式  
  
|||  
|-|-|  
|[addressof](../Topic/addressof.md)|取得物件真正的位址。|  
|[align](../Topic/align.md)|根據所提供的對齊和開始位址，傳回指向指定大小之範圍的指標。|  
|[allocate\_shared](../Topic/allocate_shared.md)|建立  `shared_ptr`，指向透過指定的配置器為特定類型配置及建構的物件。|  
|[checked\_uninitialized\_copy](../misc/checked-uninitialized-copy.md)|與 `uninitialized_copy` 相同，但是強制使用已檢查的迭代器做為輸出迭代器。|  
|[checked\_uninitialized\_fill\_n](../misc/checked-uninitialized-fill-n.md)|與 `uninitialized_fill_n` 相同，但是強制使用已檢查的迭代器做為輸出迭代器。|  
|[const\_pointer\_cast](../Topic/const_pointer_cast.md)|常數轉型成 `shared_ptr`。|  
|[declare\_no\_pointers](../Topic/declare_no_pointers.md)|通知記憶體回收行程，在指定之位址開頭且落在指示之區塊大小內的字元不包含任何可追蹤指標。|  
|[declare\_reachable](../Topic/declare_reachable.md)|告知記憶體回收，指示的位址是前往配置儲存體且可連接。|  
|[default\_delete](../Topic/default_delete.md)|刪除使用 `operator new` 配置的物件。  適合搭配 `unique_ptr` 使用。|  
|[dynamic\_pointer\_cast](../Topic/dynamic_pointer_cast.md)|動態轉型為 `shared_ptr`。|  
|[get\_deleter](../Topic/get_deleter%20Function.md)|從 `shared_ptr` 取得刪除者。|  
|[get\_pointer\_safety](../Topic/get_pointer_safety.md)|傳回任何記憶體回收行程所假設之指標安全的類型。|  
|[get\_temporary\_buffer](../Topic/get_temporary_buffer.md)|為項目序列 \(不超過指定的項目數目\) 配置暫時儲存區。|  
|[make\_shared](../Topic/make_shared%20\(%3Cmemory%3E\).md)|建立並傳回 `shared_ptr`，它會指向使用預設配置器從零個或多個引數建構的配置物件。|  
|[make\_unique](../Topic/make_unique.md)|建立並傳回 [unique\_ptr](../standard-library/unique-ptr-class.md)，它會指向從零個或多個引數建構的配置物件。|  
|[owner\_less](../Topic/owner_less.md)|允許按擁有權混合比較共用指標和弱式指標。|  
|[pointer\_safety](../Topic/pointer_safety%20Enumeration.md)|`get_pointer_safety` 所有可能的傳回值的列舉。|  
|[return\_temporary\_buffer](../Topic/return_temporary_buffer.md)|將使用 `get_temporary_buffer` 樣板函式配置的暫存記憶體取消配置。|  
|[static\_pointer\_cast](../Topic/static_pointer_cast.md)|靜態轉型至 `shared_ptr`。|  
|[交換](../Topic/swap%20\(C++%20Standard%20Library\).md)|交換兩個 `shared_ptr` 或 `weak_ptr` 物件。|  
|[unchecked\_uninitialized\_copy](../misc/unchecked-uninitialized-copy.md)|與 `uninitialized_copy` 相同，但在定義 \_SECURE\_SCL\=1 時允許使用未檢查的迭代器做為輸出迭代器。|  
|[unchecked\_uninitialized\_fill\_n](../misc/unchecked-uninitialized-fill-n.md)|與 `uninitialized_fill_n` 相同，但在定義 \_SECURE\_SCL\=1 時允許使用未檢查的迭代器做為輸出迭代器。|  
|[undeclare\_no\_pointers](../Topic/undeclare_no_pointers.md)|通知記憶體回收行程，基底位址指標和區塊大小定義的記憶體區塊中的字元現在可能會包含可追蹤的指標。|  
|[undeclare\_reachable](../Topic/undeclare_reachable.md)|通知 `garbage_collector`，指定的記憶體位置無法連接。|  
|[uninitialized\_copy](../Topic/uninitialized_copy.md)|從指定的輸入範圍將物件複製到未初始化的目的範圍內。|  
|[uninitialized\_copy\_n](../Topic/uninitialized_copy_n.md)|從輸入迭代器建立所指定項目數的複本。  複本會放在正向迭代器中。|  
|[uninitialized\_fill](../Topic/uninitialized_fill.md)|將所指定值的物件複製到未初始化的目的範圍內。|  
|[uninitialized\_fill\_n](../Topic/uninitialized_fill_n.md)|將所指定值的物件複製到未初始化目的範圍的指定項目數內。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cmemory%3E\).md)|測試指定類別的配置器物件之間是否不等。|  
|[operator\=\=](../Topic/operator==%20\(%3Cmemory%3E\).md)|測試指定類別的配置器物件之間是否相等。|  
|[運算子 \>\=](../Topic/operator%3E=%20\(%3Cmemory%3E\).md)|測試指定之類別的一個配置器物件是否大於或等於第二個配置器物件。|  
|[運算子 \<](../Topic/operator%3C%20\(%3Cmemory%3E\).md)|測試指定之類別的一個物件是否小於第二個物件。|  
|[運算子 \<\=](../Topic/operator%3C=%20\(%3Cmemory%3E\).md)|測試指定之類別的一個物件是否小於或等於第二個物件。|  
|[運算子 \>](../Topic/operator%3E%20\(%3Cmemory%3E\).md)|測試指定之類別的一個物件是否大於第二個物件。|  
|[運算子 \<\<](../Topic/operator%3C%3C%20\(%3Cmemory%3E\).md)|`shared_ptr` 插入者。|  
  
### 類別  
  
|||  
|-|-|  
|[allocator](../standard-library/allocator-class.md)|此樣板類別描述物件，該物件管理 **Type** 類型物件陣列的儲存空間配置和釋放。|  
|[allocator\_traits](../standard-library/allocator-traits-class.md)|描述物件，用來判斷啟用配置器之容器所需的所有資訊。|  
|[auto\_ptr](../standard-library/auto-ptr-class.md)|此樣板類別描述物件，該物件儲存類型 **Type \*** 之配置物件的指標，保證所指向的物件會在其封入 auto\_ptr 終結時被刪除。|  
|[bad\_weak\_ptr](../standard-library/bad-weak-ptr-class.md)|報告錯誤 weak\_ptr 例外狀況。|  
|[enabled\_shared\_from\_this](../standard-library/enable-shared-from-this-class.md)|幫助產生 `shared_ptr`。|  
|[pointer\_traits](../standard-library/pointer-traits-struct.md)|提供樣板類別 `allocator_traits` 的物件所需的資訊，以描述具有指標類型 `Ptr` 的配置器。|  
|[raw\_storage\_iterator](../standard-library/raw-storage-iterator-class.md)|提供的配接器類別，可讓演算法將其結果儲存至未初始化的記憶體。|  
|[shared\_ptr](../standard-library/shared-ptr-class.md)|將參考計數的智慧型指標環繞動態配置物件。|  
|[unique\_ptr](../standard-library/unique-ptr-class.md)|儲存自有物件的指標。  沒有任何其他 `unique_ptr` 擁有此指標。  終結擁有者時，也會終結 `unique_ptr`。|  
|[weak\_ptr](../standard-library/weak-ptr-class.md)|包裝弱式連結的指標。|  
  
### 特製化  
  
|||  
|-|-|  
|[allocator\<void\>](../standard-library/allocator-void-class.md)|void 類型的樣板類別配置器特製化，只用於定義在此特殊內容中具有意義的成員形別。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)