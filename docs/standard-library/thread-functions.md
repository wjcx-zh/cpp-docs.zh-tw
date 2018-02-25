---
title: "&lt;thread&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: 54e4c09c7db5fb29cdfb067b47d8584451277d4a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt; 函式
||||  
|-|-|-|  
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|  
|[swap](#swap)|[yield](#yield)|  
  
##  <a name="get_id"></a>  get_id  
 可唯一識別執行目前的執行緒。  
  
```  
thread::id this_thread::get_id() noexcept;  
```  
  
### <a name="return-value"></a>傳回值  
 [thread:: id](../standard-library/thread-class.md) 類型的物件，可唯一識別執行目前的執行緒。  
  
##  <a name="sleep_for"></a>  sleep_for  
 封鎖呼叫執行緒。  
  
```  
template <class Rep,  
class Period>  
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>參數  
 `Rel_time`  
 [duration](../standard-library/duration-class.md) 物件，可指定時間間隔。  
  
### <a name="remarks"></a>備註  
 函式會封鎖呼叫執行緒，至少是 `Rel_time` 指定的時間。 這個函式不會擲回任何例外狀況。  
  
##  <a name="sleep_until"></a>  sleep_until  
 封鎖呼叫執行緒，至少直到指定的時間。  
  
```  
template <class Clock, class Duration>  
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```  
  
### <a name="parameters"></a>參數  
 `Abs_time`  
 表示時間點。  
  
### <a name="remarks"></a>備註  
 這個函式不會擲回任何例外狀況。  
  
##  <a name="swap"></a>  swap  
 交換兩個 `thread` 物件的狀態。  
  
```  
void swap(thread& Left, thread& Right) noexcept;  
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `thread` 物件。  
  
 `Right`  
 右 `thread` 物件。  
  
### <a name="remarks"></a>備註  
 此函式會呼叫 `Left.swap(Right)`。  
  
##  <a name="yield"></a>  yield  
 向作業系統表示執行其他執行緒，即使目前的執行緒通常會繼續執行。  
  
```  
inline void yield() noexcept;  
```  
  
## <a name="see-also"></a>請參閱  
 [\<thread>](../standard-library/thread.md)

