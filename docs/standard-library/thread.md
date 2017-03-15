---
title: "&lt;執行緒&gt;|Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 9b32de86d2ec84017157cccf1a05b9e9b6802e47
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt"></a>&lt;執行緒&gt;
包含標準標頭\<執行緒 > 定義類別`thread`和各種支援的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  使用已編譯的程式碼中**/clr**，此標頭會封鎖。  
  
 `__STDCPP_THREADS__`巨集定義為非零值，指出執行緒會受到此標頭。  
  
## <a name="members"></a>Members  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|說明|  
|----------|-----------------|  
|[thread 類別](../standard-library/thread-class.md)|定義用來觀察和管理應用程式中執行的執行緒的物件。|  
  
### <a name="public-structures"></a>公用結構  
  
|名稱|描述|  
|----------|-----------------|  
|[hash 結構 (C++ 標準程式庫)](../standard-library/hash-structure-stl.md)|定義成員函式的傳回值，唯一取決於`thread::id`。 成員函式定義[雜湊](../standard-library/hash-class.md)適用於類型的對應值的函式`thread::id`索引值的分佈。|  
  
### <a name="public-functions"></a>公用函式  
  
|名稱|說明|  
|----------|-----------------|  
|[get_id 函式](../standard-library/thread-functions.md#get_id_function)|可唯一識別執行目前的執行緒。|  
|[sleep_for 函式](../standard-library/thread-functions.md#sleep_for_function)|封鎖呼叫執行緒。|  
|[sleep_until 函式](../standard-library/thread-functions.md#sleep_until_function)|封鎖呼叫執行緒，至少直到指定的時間。|  
|[swap 函式](../standard-library/thread-functions.md#swap_function)|交換兩個狀態`thread`物件。|  
|[yield 函式](../standard-library/thread-functions.md#yield_function)|向作業系統表示執行其他執行緒，即使目前的執行緒通常會繼續執行。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[運算子 > = 運算子](../standard-library/thread-operators.md#operator_gt__eq)|判斷某個 `thread::id` 物件是否大於或等於另一個。|  
|[運算子 > 運算子](../standard-library/thread-operators.md#operator_gt_)|判斷某個 `thread::id` 物件是否大於另一個。|  
|[運算子<=></=>](../standard-library/thread-operators.md#operator_lt__eq)|判斷某個 `thread::id` 物件是否小於或等於另一個。|  
|[運算子<>](../standard-library/thread-operators.md#operator_lt_)|判斷某個 `thread::id` 物件是否小於另一個。|  
|[運算子 ！ = 運算子](../standard-library/thread-operators.md#operator_neq)|比較兩個 `thread::id` 物件是否不相等。|  
|[運算子 = = 運算子](../standard-library/thread-operators.md#operator_eq_eq)|比較兩個 `thread::id` 物件是否相等。|  
|[運算子<>](../standard-library/thread-operators.md#operator_lt__lt_)|將 `thread::id` 物件的文字表示插入資料流。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


