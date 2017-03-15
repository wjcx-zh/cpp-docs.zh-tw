---
title: "recursive_mutex 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::recursive_mutex
dev_langs:
- C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c82c8302be5d3e01de90adda2049a022100b8443
ms.lasthandoff: 02/24/2017

---
# <a name="recursivemutex-class"></a>recursive_mutex 類別
代表 mutex 類型。 相較於 [mutex](../standard-library/mutex-class-stl.md)，已針對已經鎖定的物件妥善定義呼叫鎖定方法的行為。  
  
## <a name="syntax"></a>語法  
  
```
class recursive_mutex;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[recursive_mutex 建構函式](#recursive_mutex__recursive_mutex_constructor)|建構 `recursive_mutex` 物件。|  
|[~recursive_mutex 解構函式](#recursive_mutex___dtorrecursive_mutex_destructor)|釋放 `recursive_mutex` 物件使用的所有資源。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[lock](#recursive_mutex__lock_method)|在呼叫執行緒取得 mutex 的擁有權之前，封鎖該執行緒。|  
|[try_lock](#recursive_mutex__try_lock_method)|嘗試在不封鎖 mutex 的情況下，取得它的擁有權。|  
|[unlock](#recursive_mutex__unlock_method)|釋放 mutex 的擁有權。|  
  
## <a name="requirements"></a>需求  
 **標頭：**mutex  
  
 **命名空間：** std  
  
##  <a name="a-namerecursivemutexlockmethoda--lock"></a><a name="recursive_mutex__lock_method"></a>  lock  
 封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫執行緒已經擁有 `mutex`，方法會立即傳回，而先前的鎖定仍持續有效。  
  
##  <a name="a-namerecursivemutexrecursivemutexconstructora--recursivemutex"></a><a name="recursive_mutex__recursive_mutex_constructor"></a>  recursive_mutex  
 建構未鎖定的 `recursive_mutex` 物件。  
  
```cpp  
recursive_mutex();
```  
  
##  <a name="a-namerecursivemutexdtorrecursivemutexdestructora--recursivemutex"></a><a name="recursive_mutex___dtorrecursive_mutex_destructor"></a>  ~recursive_mutex  
 釋放物件使用的所有資源。  
  
```cpp  
~recursive_mutex();
```  
  
### <a name="remarks"></a>備註  
 如果執行解構函式時物件已鎖定，則行為是未定義的。  
  
##  <a name="a-namerecursivemutextrylockmethoda--trylock"></a><a name="recursive_mutex__try_lock_method"></a>  try_lock  
 嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功取得 `mutex` 的擁有權，或是呼叫執行緒已經擁有 `mutex`，即為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 如果呼叫執行緒已經擁有 `mutex`，函式會立即傳回 `true`，而先前的鎖定仍持續有效。  
  
##  <a name="a-namerecursivemutexunlockmethoda--unlock"></a><a name="recursive_mutex__unlock_method"></a>  unlock  
 釋放 mutex 的擁有權。  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>備註  
 這個方法只會在呼叫它的次數與在 `recursive_mutex` 物件上成功呼叫 [lock](#recursive_mutex__lock_method) 和 [try_lock](#recursive_mutex__try_lock_method) 的次數一樣多之後，才會釋放 `mutex` 的擁有權。  
  
 如果呼叫的執行緒未擁有 `mutex`，則行為是未定義的。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




