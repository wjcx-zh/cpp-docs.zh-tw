---
title: "mutex 類別 (C++ 標準程式庫)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::mutex
dev_langs:
- C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: 11
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
ms.openlocfilehash: ff3e7e71c678ffc9bdead79ec56ad94f8e297a16
ms.lasthandoff: 02/24/2017

---
# <a name="mutex-class-c-standard-library"></a>mutex 類別 (C++ 標準程式庫)
代表「mutex 類型」。 這個類型的物件可以用來強制程式內的互斥。  
  
## <a name="syntax"></a>語法  
  
```
class mutex;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[mutex::mutex 建構函式](#mutex__mutex_constructor)|建構 `mutex` 物件。|  
|[mutex::~mutex 解構函式](#mutex___dtormutex_destructor)|釋放 `mutex` 物件使用的所有資源。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[mutex::lock 方法](#mutex__lock_method)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|  
|[mutex::native_handle 方法](#mutex__native_handle_method)|傳回表示 mutex 控制代碼的實作特定類型。|  
|[mutex::try_lock 方法](#mutex__try_lock_method)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|  
|[mutex::unlock 方法](#mutex__unlock_method)|釋放 `mutex` 的擁有權。|  
  
## <a name="requirements"></a>需求  
 **標頭：**mutex  
  
 **命名空間：** std  
  
##  <a name="a-namemutexlockmethoda--mutexlock-method"></a><a name="mutex__lock_method"></a>  mutex::lock 方法  
 封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。  
  
##  <a name="a-namemutexmutexconstructora--mutexmutex-constructor"></a><a name="mutex__mutex_constructor"></a>  mutex::mutex 建構函式  
 建構未鎖定的 `mutex` 物件。  
  
```cpp  
constexpr mutex() noexcept;
```  
  
##  <a name="a-namemutexdtormutexdestructora--mutexmutex-destructor"></a><a name="mutex___dtormutex_destructor"></a>  mutex::~mutex 解構函式  
 釋出 `mutex` 物件所使用的任何資源。  
  
```cpp  
~mutex();
```  
  
### <a name="remarks"></a>備註  
 如果執行解構函式時物件已鎖定，則行為是未定義的。  
  
##  <a name="a-namemutexnativehandlemethoda--mutexnativehandle-method"></a><a name="mutex__native_handle_method"></a>  mutex::native_handle 方法  
 傳回表示 mutex 控制代碼的實作特定類型。 您可以利用實作特定的方式來使用 mutex 控制代碼。  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>傳回值  
 `native_handle_type` 會定義為 `Concurrency::critical_section *`，這會轉換為 `void *`。  
  
##  <a name="a-namemutextrylockmethoda--mutextrylock-method"></a><a name="mutex__try_lock_method"></a>  mutex::try_lock 方法  
 嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。  
  
```cpp  
bool try_lock();
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功取得 `true` 的擁有權，就是 `mutex`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。  
  
##  <a name="a-namemutexunlockmethoda--mutexunlock-method"></a><a name="mutex__unlock_method"></a>  mutex::unlock 方法  
 釋放 `mutex` 的擁有權。  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的執行緒未擁有 `mutex`，則行為是未定義的。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




