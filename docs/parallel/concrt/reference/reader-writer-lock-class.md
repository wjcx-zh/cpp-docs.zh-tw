---
title: "reader_writer_lock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
dev_langs:
- C++
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: b5107923baa7d22e6a98c6617a22a883c4d84125
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="readerwriterlock-class"></a>reader_writer_lock 類別
以寫入器偏好設定佇列為基礎且只能本機微調的讀取器-寫入器鎖定。 鎖定會授與寫入器先進先出 (FIFO) 存取權，並在連續載入寫入器的情況下影響讀取器。  
  
## <a name="syntax"></a>語法  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|描述|  
|----------|-----------------|  
|[reader_writer_lock 類別](#scoped_lock_class)|例外狀況安全 RAII 包裝函式可以用來取得`reader_writer_lock`成為寫入器鎖定的物件。|  
|[reader_writer_lock 類別](#scoped_lock_read_class)|例外狀況安全 RAII 包裝函式可以用來取得`reader_writer_lock`讀取器鎖定的物件。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|建構新`reader_writer_lock`物件。|  
|[~ reader_writer_lock 解構函式](#dtor)|終結`reader_writer_lock`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[lock](#lock)|取得讀取器-寫入器的鎖定做為寫入器。|  
|[lock_read](#lock_read)|讀取器取得讀取器-寫入器鎖定。 如果寫入器，使用中的讀取器必須等到它們完成。 讀取器只會註冊之鎖定，並等待釋放它的寫入器。|  
|[try_lock](#try_lock)|嘗試寫入器，以取得讀取器-寫入器鎖定，而不封鎖。|  
|[try_lock_read](#try_lock_read)|嘗試取得讀取器讀取器-寫入器鎖定，而不會封鎖。|  
|[unlock](#unlock)|根據使用者鎖定、 讀取或寫入器的讀取器-寫入器鎖定會解除鎖定。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `reader_writer_lock`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="lock"></a>鎖定 

 取得讀取器-寫入器的鎖定做為寫入器。  
  
```
void lock();
```  
  
### <a name="remarks"></a>備註  
 通常是安全的作法是利用[scoped_lock](#scoped_lock_class)建構函式來取得及釋放`reader_writer_lock`物件做為寫入器擲回例外狀況安全的方式。  
  
 寫入器嘗試取得鎖定後，後續任何讀取器都會封鎖，直到寫入器成功取得及釋放鎖定為止。 這種鎖定偏向寫入器，可以使讀取器，連續負載的寫入器匱乏。  
  
 寫入器會鏈結，以便結束鎖定的寫入器釋放列中的下一個寫入器。  
  
 如果鎖定已保留所呼叫的內容， [improper_lock](improper-lock-class.md)擲回例外狀況。  
  
##  <a name="lock_read"></a>lock_read 

 讀取器取得讀取器-寫入器鎖定。 如果寫入器，使用中的讀取器必須等到它們完成。 讀取器只會註冊之鎖定，並等待釋放它的寫入器。  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>備註  
 通常是安全的作法是利用[scoped_lock_read](#scoped_lock_read_class)建構函式來取得及釋放`reader_writer_lock`物件讀取器擲回例外狀況安全的方式。  
  
 如果發生鎖定等候的寫入器，讀取器會等到所有列中的寫入器取得及釋放鎖定。 這種鎖定偏向寫入器，可以使讀取器，連續負載的寫入器匱乏。  
  
##  <a name="ctor"></a>reader_writer_lock 

 建構新`reader_writer_lock`物件。  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a>~ reader_writer_lock 

 終結`reader_writer_lock`物件。  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>備註  
 預期解構函式執行時，不會再保留鎖定。 允許讀取器的寫入器鎖定與鎖定解構仍保留在未定義的行為結果。  
  
##  <a name="scoped_lock_class"></a>reader_writer_lock 類別  
 例外狀況安全 RAII 包裝函式可以用來取得`reader_writer_lock`成為寫入器鎖定的物件。  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock 

建構`scoped_lock`物件，並取得`reader_writer_lock`物件傳入`_Reader_writer_lock`參數做為寫入器。 如果由另一個執行緒鎖定，這個呼叫會封鎖。  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>參數  
 `_Reader_writer_lock`  
 `reader_writer_lock`成為寫入器取得的物件。  
  
## <a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock 

終結`reader_writer_lock`物件，並釋放其建構函式中提供的鎖定。   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>reader_writer_lock 類別  
 例外狀況安全 RAII 包裝函式可以用來取得`reader_writer_lock`讀取器鎖定的物件。  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a>try_lock 

 嘗試寫入器，以取得讀取器-寫入器鎖定，而不封鎖。  

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read 

建構`scoped_lock_read`物件，並取得`reader_writer_lock`物件傳入`_Reader_writer_lock`讀取器的參數。 如果由另一個執行緒成為寫入器鎖定，或有擱置的寫入器，這個呼叫會封鎖。  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>參數  
 `_Reader_writer_lock`  
 `reader_writer_lock`取得讀取器物件。  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock:: ~ scoped_lock_read 解構函式
終結`scoped_lock_read`物件，並釋放其建構函式中提供的鎖定。  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a>try_lock 

```
bool try_lock();
```  
  
### <a name="return-value"></a>傳回值  
 如果已取得鎖定，值`true`; 否則值`false`。  
  
##  <a name="try_lock_read"></a>try_lock_read 

 嘗試取得讀取器讀取器-寫入器鎖定，而不會封鎖。  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>傳回值  
 如果已取得鎖定，值`true`; 否則值`false`。  
  
##  <a name="unlock"></a>解除鎖定 

 根據使用者鎖定、 讀取或寫入器的讀取器-寫入器鎖定會解除鎖定。  
  
```
void unlock();
```  
  
### <a name="remarks"></a>備註  
 如果寫入器鎖定上等候的鎖定版本會一律前往 FIFO 順序中的下一個寫入器。 這種鎖定偏向寫入器，可以使讀取器，連續負載的寫入器匱乏。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [critical_section 類別](critical-section-class.md)

