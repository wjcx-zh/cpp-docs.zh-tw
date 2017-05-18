---
title: "mutex 類別 (C++ 標準程式庫)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: e08c7c13d1e182bc3299f11769eddb699b03ab3f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

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
|[mutex](#mutex)|建構 `mutex` 物件。|  
|[mutex::~mutex 解構函式](#dtormutex_destructor)|釋放 `mutex` 物件使用的所有資源。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[lock](#lock)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|  
|[native_handle](#native_handle)|傳回表示 mutex 控制代碼的實作特定類型。|  
|[try_lock](#try_lock)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|  
|[unlock](#unlock)|釋放 `mutex` 的擁有權。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \<mutex >  
  
 **命名空間：** std  
  
##  <a name="lock"></a>mutex:: lock
 封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。  
  
##  <a name="mutex"></a>  mutex::mutex 建構函式  
 建構未鎖定的 `mutex` 物件。  
  
```cpp  
constexpr mutex() noexcept;
```  
  
##  <a name="dtormutex_destructor"></a>  mutex::~mutex 解構函式  
 釋出 `mutex` 物件所使用的任何資源。  
  
```cpp  
~mutex();
```  
  
### <a name="remarks"></a>備註  
 如果執行解構函式時物件已鎖定，則行為是未定義的。  
  
##  <a name="native_handle"></a>mutex:: native_handle
 傳回表示 mutex 控制代碼的實作特定類型。 您可以利用實作特定的方式來使用 mutex 控制代碼。  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>傳回值  
 `native_handle_type` 會定義為 `Concurrency::critical_section *`，這會轉換為 `void *`。  
  
##  <a name="try_lock"></a>mutex:: try_lock
 嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。  
  
```cpp  
bool try_lock();
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功取得 `true` 的擁有權，就是 `mutex`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。  
  
##  <a name="unlock"></a>mutex:: unlock
 釋放 `mutex` 的擁有權。  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的執行緒未擁有 `mutex`，則行為是未定義的。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




