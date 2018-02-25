---
title: "lock_guard 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60643375742ef02ef1ba8ea08e614d12c504c573
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="lockguard-class"></a>lock_guard 類別
表示可以具現化的範本，用來建立解構函式會解除鎖定 `mutex` 的物件。  
  
## <a name="syntax"></a>語法  
  
```
template <class Mutex>
class lock_guard;
```  
  
## <a name="remarks"></a>備註  
 範本引數 `Mutex` 必須指定一個「mutex 類型」。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`lock_guard::mutex_type`|與範本引數 `Mutex` 同義。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[lock_guard](#lock_guard)|建構 `lock_guard` 物件。|  
|[lock_guard::~lock_guard 解構函式](#dtorlock_guard_destructor)|將傳遞給建構函式的 `mutex` 物件解除鎖定。|  
  
## <a name="requirements"></a>需求  
 **標頭：** \<mutex >  
  
 **命名空間：** std  
  
##  <a name="lock_guard"></a>  lock_guard::lock_guard 建構函式  
 建構 `lock_guard` 物件。  
  
```cpp  
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```  
  
### <a name="parameters"></a>參數  
 `Mtx`  
 「mutex 類型」物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會建構 `lock_guard` 類型並且會鎖定 `Mtx` 的物件。 如果 `Mtx` 不是遞迴 mutex，則呼叫此建構函式時，就必須將它解除鎖定。  
  
 第二個建構函式不會鎖定 `Mtx`。 呼叫此建構函式時，必須鎖定 `Mtx`。 此建構函式不會擲回任何例外狀況。  
  
##  <a name="dtorlock_guard_destructor"></a>  lock_guard::~lock_guard 解構函式  
 將傳遞給建構函式的 `mutex` 物件解除鎖定。  
  
```
~lock_guard() noexcept;
```  
  
### <a name="remarks"></a>備註  
 針對執行解構函式時 `mutex` 不存在的情況，並未定義此行為。  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



