---
title: '&lt;thread&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa16f2f06a55122619741c5889f41ce3d6b53c1e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltthreadgt"></a>&lt;thread&gt;
包含標準標頭\<執行緒 > 若要定義類別`thread`和各種支援的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  使用編譯的程式碼中**/clr**，此標頭會遭到封鎖。  
  
 `__STDCPP_THREADS__`巨集定義為非零值，指出執行緒會受到此標頭。  
  
## <a name="members"></a>成員  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|描述|  
|----------|-----------------|  
|[thread 類別](../standard-library/thread-class.md)|定義用來觀察和管理應用程式中執行的執行緒的物件。|  
  
### <a name="public-structures"></a>公用結構  
  
|名稱|描述|  
|----------|-----------------|  
|[hash 結構 (C++ 標準程式庫)](../standard-library/hash-structure-stl.md)|定義成員函式的傳回值，唯一取決於`thread::id`。 成員函式定義[雜湊](../standard-library/hash-class.md)適用於類型的對應值的函式`thread::id`索引值的分佈。|  
  
### <a name="public-functions"></a>公用函式  
  
|名稱|描述|  
|----------|-----------------|  
|[get_id](../standard-library/thread-functions.md#get_id)|可唯一識別執行目前的執行緒。|  
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|封鎖呼叫執行緒。|  
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|封鎖呼叫執行緒，至少直到指定的時間。|  
|[swap](../standard-library/thread-functions.md#swap)|交換兩個狀態`thread`物件。|  
|[yield](../standard-library/thread-functions.md#yield)|向作業系統表示執行其他執行緒，即使目前的執行緒通常會繼續執行。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[運算子 > = 運算子](../standard-library/thread-operators.md#op_gt_eq)|判斷某個 `thread::id` 物件是否大於或等於另一個。|  
|[運算子 > 運算子](../standard-library/thread-operators.md#op_gt)|判斷某個 `thread::id` 物件是否大於另一個。|  
|[operator<= Operator](../standard-library/thread-operators.md#op_lt_eq)|判斷某個 `thread::id` 物件是否小於或等於另一個。|  
|[運算子 < 運算子](../standard-library/thread-operators.md#op_lt)|判斷某個 `thread::id` 物件是否小於另一個。|  
|[運算子 ！ = 運算子](../standard-library/thread-operators.md#op_neq)|比較兩個 `thread::id` 物件是否不相等。|  
|[operator== Operator](../standard-library/thread-operators.md#op_eq_eq)|比較兩個 `thread::id` 物件是否相等。|  
|[運算子 << 運算子](../standard-library/thread-operators.md#op_lt_lt)|將 `thread::id` 物件的文字表示插入資料流。|  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

