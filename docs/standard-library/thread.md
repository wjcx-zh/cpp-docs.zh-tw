---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 251a423829a048e3d67b0bcf83107f52c3fdafca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232842"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

包含標準標頭， \<thread> 以定義類別 `thread` 和各種支援的函式。

## <a name="syntax"></a>語法

```cpp
#include <thread>
```

## <a name="remarks"></a>備註

> [!NOTE]
> 在使用 **/clr**編譯的程式碼中，此標頭會遭到封鎖。

`__STDCPP_THREADS__`宏會定義為非零值，表示此標頭支援執行緒。

## <a name="members"></a>成員

### <a name="public-classes"></a>公用類別

|名稱|說明|
|----------|-----------------|
|[thread 類別](../standard-library/thread-class.md)|定義物件，用來觀察和管理應用程式中的執行執行緒。|

### <a name="public-structures"></a>公用結構

|名稱|說明|
|----------|-----------------|
|[hash 結構 (C++ 標準程式庫)](../standard-library/hash-structure-stl.md)|定義會傳回唯一由所決定之值的成員函式 `thread::id` 。 此成員函式會定義[雜湊](../standard-library/hash-class.md)函式，適用于將類型的值對應 `thread::id` 到索引值的分佈。|

### <a name="public-functions"></a>公用函式

|名稱|說明|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|可唯一識別執行目前的執行緒。|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|封鎖呼叫執行緒。|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|封鎖呼叫執行緒，至少直到指定的時間。|
|[調換](../standard-library/thread-functions.md#swap)|交換兩個物件的狀態 `thread` 。|
|[yield](../standard-library/thread-functions.md#yield)|向作業系統表示執行其他執行緒，即使目前的執行緒通常會繼續執行。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[運算子>= 運算子](../standard-library/thread-operators.md#op_gt_eq)|判斷某個 `thread::id` 物件是否大於或等於另一個。|
|[運算子> 運算子](../standard-library/thread-operators.md#op_gt)|判斷某個 `thread::id` 物件是否大於另一個。|
|[運算子<= 運算子](../standard-library/thread-operators.md#op_lt_eq)|判斷某個 `thread::id` 物件是否小於或等於另一個。|
|[運算子< 運算子](../standard-library/thread-operators.md#op_lt)|判斷某個 `thread::id` 物件是否小於另一個。|
|[operator！ = 運算子](../standard-library/thread-operators.md#op_neq)|比較兩個 `thread::id` 物件是否不相等。|
|[operator = = 運算子](../standard-library/thread-operators.md#op_eq_eq)|比較兩個 `thread::id` 物件是否相等。|
|[運算子<< 運算子](../standard-library/thread-operators.md#op_lt_lt)|將 `thread::id` 物件的文字表示插入資料流。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
