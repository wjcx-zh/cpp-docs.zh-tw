---
title: reader_writer_lock 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2f48a80efca0ec6e85a315b355a6482fb2096b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="readerwriterlock-class"></a>reader_writer_lock 類別
以寫入器偏好設定佇列為基礎且只能本機微調的讀取器-寫入器鎖定。 鎖定會授與寫入器先進先出 (FIFO) 存取權，並在連續載入寫入器的情況下影響讀取器。  
  
## <a name="syntax"></a>語法  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|描述|  
|----------|-----------------|  
|[reader_writer_lock:: scoped_lock 類別](#scoped_lock_class)|例外狀況安全 RAII 包裝函式，可以用來取得`reader_writer_lock`成為寫入器鎖定的物件。|  
|[reader_writer_lock:: scoped_lock_read 類別](#scoped_lock_read_class)|例外狀況安全 RAII 包裝函式，可以用來取得`reader_writer_lock`為讀取器鎖定的物件。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|建構新`reader_writer_lock`物件。|  
|[~ reader_writer_lock 解構函式](#dtor)|終結`reader_writer_lock`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[lock](#lock)|取得讀取器-寫入器的鎖定做為寫入器。|  
|[lock_read](#lock_read)|取得讀取器-寫入器的鎖定以讀者身分。 如果寫入器，使用中的讀取器必須請等到它們完成。 讀取器只會註冊鎖定有興趣，並等待釋放它的寫入器。|  
|[try_lock](#try_lock)|嘗試寫入器，以取得讀取器-寫入器鎖定，而不封鎖。|  
|[try_lock_read](#try_lock_read)|嘗試以讀者身分取得讀取器-寫入器鎖定，而不會封鎖。|  
|[unlock](#unlock)|解除鎖定者鎖定、 讀取器或寫入器為基礎的讀取器-寫入器鎖定。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `reader_writer_lock`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="lock"></a> 鎖定 

 取得讀取器-寫入器的鎖定做為寫入器。  
  
```
void lock();
```  
  
### <a name="remarks"></a>備註  
 通常是安全的作法是利用[scoped_lock](#scoped_lock_class)建構函式來取得並發行`reader_writer_lock`物件做為寫入器，其例外狀況安全的方式。  
  
 寫入器嘗試取得鎖定後，後續任何讀取器都會封鎖，直到寫入器成功取得及釋放鎖定為止。 這個鎖定變成優先寫入器，而導致在連續載入寫入器下的讀取器。  
  
 寫入器會鏈結，以便結束鎖定的寫入器釋放列中的下一個寫入器。  
  
 如果程式在呼叫端的內容，就已經持有鎖定[improper_lock](improper-lock-class.md)擲回例外狀況。  
  
##  <a name="lock_read"></a> lock_read 

 取得讀取器-寫入器的鎖定以讀者身分。 如果寫入器，使用中的讀取器必須請等到它們完成。 讀取器只會註冊鎖定有興趣，並等待釋放它的寫入器。  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>備註  
 通常是安全的作法是利用[scoped_lock_read](#scoped_lock_read_class)建構函式來取得並發行`reader_writer_lock`物件做為讀取器例外狀況安全的方式。  
  
 如果正在等候鎖定的寫入器，讀取器會等待所有列中的寫入器具有取得和釋放鎖定。 這個鎖定變成優先寫入器，而導致在連續載入寫入器下的讀取器。  
  
##  <a name="ctor"></a> reader_writer_lock 

 建構新`reader_writer_lock`物件。  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a> ~ reader_writer_lock 

 終結`reader_writer_lock`物件。  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>備註  
 預期解構函式執行時，不會再保留鎖定。 允許讀取器的寫入器鎖定與鎖定解構仍保留未定義的行為結果。  
  
##  <a name="scoped_lock_class"></a>  reader_writer_lock:: scoped_lock 類別  
 例外狀況安全 RAII 包裝函式，可以用來取得`reader_writer_lock`成為寫入器鎖定的物件。  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock 

建構`scoped_lock`物件，並取得`reader_writer_lock`物件傳入`_Reader_writer_lock`成為寫入器的參數。 如果另一個執行緒鎖定，此呼叫將會封鎖。  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>參數  
 `_Reader_writer_lock`  
 `reader_writer_lock`成為寫入器取得的物件。  
  
## <a name="scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock 

終結`reader_writer_lock`物件，並釋放其建構函式中所提供的鎖定。   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>  reader_writer_lock:: scoped_lock_read 類別  
 例外狀況安全 RAII 包裝函式，可以用來取得`reader_writer_lock`為讀取器鎖定的物件。  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a> try_lock 

 嘗試寫入器，以取得讀取器-寫入器鎖定，而不封鎖。  

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read 

建構`scoped_lock_read`物件，並取得`reader_writer_lock`物件傳入`_Reader_writer_lock`參數做為讀取器。 如果寫入器的另一個執行緒鎖定，或有暫止的寫入器，這個呼叫會封鎖。  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>參數  
 `_Reader_writer_lock`  
 `reader_writer_lock`為讀取器取得的物件。  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read 解構函式
終結`scoped_lock_read`物件，並釋放其建構函式中所提供的鎖定。  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a> try_lock 

```
bool try_lock();
```  
  
### <a name="return-value"></a>傳回值  
 取得鎖定時，如果值`true`; 否則值`false`。  
  
##  <a name="try_lock_read"></a> try_lock_read 

 嘗試以讀者身分取得讀取器-寫入器鎖定，而不會封鎖。  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>傳回值  
 取得鎖定時，如果值`true`; 否則值`false`。  
  
##  <a name="unlock"></a> 解除鎖定 

 解除鎖定者鎖定、 讀取器或寫入器為基礎的讀取器-寫入器鎖定。  
  
```
void unlock();
```  
  
### <a name="remarks"></a>備註  
 如果寫入器正在等候鎖定，鎖定的版本會一律前往 FIFO 順序的下一個寫入器。 這個鎖定變成優先寫入器，而導致在連續載入寫入器下的讀取器。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [critical_section 類別](critical-section-class.md)
