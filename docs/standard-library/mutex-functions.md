---
title: "&lt;mutex&gt; 函式和變數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: 8fcee8ec1313a153764c94a709e32b3a6109b576
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; 函式和變數
||||  
|-|-|-|  
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|  
|[lock](#lock)|[try_to_lock](#try_to_lock)|  
  
##  <a name="adopt_lock"></a>  adopt_lock 變數  
 代表可傳遞給 [lock_guard](../standard-library/lock-guard-class.md) 和 [unique_lock](../standard-library/unique-lock-class.md) 之建構函式的物件，用來指出一併傳遞給建構函式的 mutex 物件已鎖定。  
  
```cpp  
const adopt_lock_t adopt_lock;
```  
  
##  <a name="call_once"></a>  call_once  
 提供用來呼叫指定之可呼叫物件一次執行期間的機制。  
  
```
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```  
  
### <a name="parameters"></a>參數  
 `Flag`  
 [once_flag](../standard-library/once-flag-structure.md) 物件，可確保只呼叫可呼叫的物件一次。  
  
 `F`  
 可呼叫的物件。  
  
 `A`  
 引數清單。  
  
### <a name="remarks"></a>備註  
 如果 `Flag` 無效，此函式就會擲回一個錯誤碼為 `invalid_argument` 的 [system_error](../standard-library/system-error-class.md)。 否則，此範本函式會使用其 `Flag` 引數，來確保不論此範本函式被呼叫多少次，它都只確切成功呼叫 `F(A...)` 一次。 如果 `F(A...)` 透過擲回例外狀況來結束，即表示該呼叫不成功。  
  
##  <a name="defer_lock"></a>  defer_lock 變數  
 代表可傳遞給 [unique_lock](../standard-library/unique-lock-class.md) 之建構函式的物件。 這會指出建構函式不應將一併傳遞給它的 mutex 物件鎖定。  
  
```cpp  
const defer_lock_t defer_lock;
```  
  
##  <a name="lock"></a>  lock  
 會嘗試鎖定所有不包含死結的引數。  
  
```cpp  
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```  
  
### <a name="remarks"></a>備註  
 此範本函式的引數必須是「mutex 類型」，但對 `try_lock` 的呼叫可能會擲回例外狀況。  
  
 此函式會藉由對 `lock`、`try_lock` 及 `unlock` 的呼叫，在不造成死結的情況下，鎖定其所有引數。 如果對 `lock` 或 `try_lock` 的呼叫擲回例外狀況，此函式就會先在任何先前已成功鎖定的 mutex 物件上呼叫 `unlock`，然後才重新擲回例外狀況。  
  
##  <a name="try_to_lock"></a>  try_to_lock Variable  
 代表可傳遞給 [unique_lock](../standard-library/unique-lock-class.md) 之建構函式的物件，用來指出建構函式應嘗試將一併傳遞給它的 `mutex` 解除鎖定而不封鎖。  
  
```cpp  
const try_to_lock_t try_to_lock;
```  
  
## <a name="see-also"></a>請參閱  
 [\<mutex>](../standard-library/mutex.md)



