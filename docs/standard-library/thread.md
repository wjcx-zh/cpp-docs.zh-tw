---
title: "&lt; 執行緒 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<thread>"
dev_langs: 
  - "C++"
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt; 執行緒 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含標準標頭 \< 執行緒> 定義類別 `thread` 和各種支援的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  使用編譯的程式碼中 **/clr** 或 **/clr: pure**, ，此標頭會封鎖。  
  
  `__STDCPP_THREADS__` 巨集定義為非零值，指出執行緒會受到此標頭。  
  
## <a name="members"></a>Members  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|描述|  
|----------|-----------------|  
|[thread 類別](../standard-library/thread-class.md)|定義用來觀察和管理應用程式中執行的執行緒的物件。|  
  
### <a name="public-structures"></a>公用結構  
  
|名稱|描述|  
|----------|-----------------|  
|[hash 結構 (STL)](../standard-library/hash-structure-stl.md)|定義成員函式的傳回值，唯一取決於 `thread::id`。 成員函式定義 [雜湊](../standard-library/hash-class.md) 適用於類型的對應值的函式 `thread::id` 索引值的分佈。|  
  
### <a name="public-functions"></a>公用函式  
  
|名稱|描述|  
|----------|-----------------|  
|[get_id 函式](../Topic/%3Cthread%3E%20functions.md#get_id_function)|可唯一識別目前的執行緒。|  
|[sleep_for 函式](../Topic/%3Cthread%3E%20functions.md#sleep_for_function)|封鎖呼叫執行緒。|  
|[sleep_until 函式](../Topic/%3Cthread%3E%20functions.md#sleep_until_function)|最少封鎖呼叫執行緒，直到指定的時間。|  
|[swap 函式](../Topic/%3Cthread%3E%20functions.md#swap_function)|交換兩個狀態 `thread` 物件。|  
|[yield 函式](../Topic/%3Cthread%3E%20functions.md#yield_function)|即使目前的執行緒通常會繼續執行，則表示執行其他執行緒的作業系統。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[運算子 > = 運算子](../Topic/%3Cthread%3E%20operators.md#operator_gt__eq)|判斷是否有一個 `thread::id` 物件是否大於或等於另一個。|  
|[運算子 > 運算子](../Topic/%3Cthread%3E%20operators.md#operator_gt_)|判斷是否有一個 `thread::id` 物件是否大於另一個。|  
|[運算子 < = 運算子](../Topic/%3Cthread%3E%20operators.md#operator_lt__eq)|判斷是否有一個 `thread::id` 物件是否小於或等於另一個。|  
|[運算子 < 運算子](../Topic/%3Cthread%3E%20operators.md#operator_lt_)|判斷是否有一個 `thread::id` 物件是否小於另一個。|  
|[運算子 ！ = 運算子](../Topic/%3Cthread%3E%20operators.md#operator_neq)|比較兩個 `thread::id` 物件是否不相等。|  
|[運算子 = = 運算子](../Topic/%3Cthread%3E%20operators.md#operator_eq_eq)|比較兩個 `thread::id` 物件是否相等。|  
|[運算子 << 運算子](../Topic/%3Cthread%3E%20operators.md#operator_lt__lt_)|插入的文字表示 `thread::id` 成資料流的物件。|  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

