---
title: reader_writer_lock 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 111d48b9c4a575078f2342bfaa944871bbd628f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394334"
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
|[reader_writer_lock:: scoped_lock 類別](#scoped_lock_class)|例外狀況安全 RAII 包裝函式，可用來取得`reader_writer_lock`成為寫入器鎖定的物件。|
|[reader_writer_lock:: scoped_lock_read 類別](#scoped_lock_read_class)|例外狀況安全 RAII 包裝函式，可用來取得`reader_writer_lock`讀者鎖定物件。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[reader_writer_lock](#ctor)|建構新`reader_writer_lock`物件。|
|[~ reader_writer_lock 解構函式](#dtor)|終結`reader_writer_lock`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[lock](#lock)|取得讀取器-寫入器鎖定為寫入器。|
|[lock_read](#lock_read)|取得讀取器-寫入器鎖定為讀取器。 如果寫入器，使用中的讀取器必須等到它們完成。 讀取器只會註冊感興趣的鎖定，並等候釋放它的寫入器。|
|[try_lock](#try_lock)|嘗試取得 reader-writer 鎖定為寫入器，而不會封鎖。|
|[try_lock_read](#try_lock_read)|嘗試取得讀者 reader-writer 鎖定，而不會封鎖。|
|[unlock](#unlock)|根據使用者鎖定，讀取器或寫入 reader-writer 鎖定會解除鎖定。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`reader_writer_lock`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="lock"></a> 鎖定

取得讀取器-寫入器鎖定為寫入器。

```
void lock();
```

### <a name="remarks"></a>備註

它通常是安全的作法是利用[scoped_lock](#scoped_lock_class)建構函式來取得和釋放`reader_writer_lock`物件作為例外狀況的寫入器安全的方式。

寫入器嘗試取得鎖定後，後續任何讀取器都會封鎖，直到寫入器成功取得及釋放鎖定為止。 這個鎖定偏向寫入器，將會佔用連續載入寫入器在讀取器。

寫入器會鏈結，以便結束鎖定的寫入器版本列在下一步 的寫入器。

如果所呼叫的內容中，已進行鎖定[improper_lock](improper-lock-class.md)會擲回例外狀況。

##  <a name="lock_read"></a> lock_read

取得讀取器-寫入器鎖定為讀取器。 如果寫入器，使用中的讀取器必須等到它們完成。 讀取器只會註冊感興趣的鎖定，並等候釋放它的寫入器。

```
void lock_read();
```

### <a name="remarks"></a>備註

它通常是安全的作法是利用[scoped_lock_read](#scoped_lock_read_class)建構函式來取得和釋放`reader_writer_lock`物件作為例外狀況的讀取器安全的方式。

如果沒有正在等候鎖定的寫入器，讀取器會等到行中的所有寫入器已取得及釋放鎖定。 這個鎖定偏向寫入器，將會佔用連續載入寫入器在讀取器。

##  <a name="ctor"></a> reader_writer_lock

建構新`reader_writer_lock`物件。

```
reader_writer_lock();
```

##  <a name="dtor"></a> ~reader_writer_lock

終結`reader_writer_lock`物件。

```
~reader_writer_lock();
```

### <a name="remarks"></a>備註

預期的是解構函式執行時，不會再保留鎖定。 允許讀取器的寫入器鎖定，來解構的鎖定仍保留在未定義的行為結果。

##  <a name="scoped_lock_class"></a>  reader_writer_lock:: scoped_lock 類別

例外狀況安全 RAII 包裝函式，可用來取得`reader_writer_lock`成為寫入器鎖定的物件。

```
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock

建構`scoped_lock`物件，並取得`reader_writer_lock`傳入物件`_Reader_writer_lock`參數寫入器。 如果鎖定維持時間由另一個執行緒，將會封鎖這個呼叫。

```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

#### <a name="parameters"></a>參數

*_Reader_writer_lock*<br/>
`reader_writer_lock`成為寫入器取得的物件。

## <a name="scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

終結`reader_writer_lock`物件，並釋放其建構函式中所提供的鎖定。

```
~scoped_lock();
```

##  <a name="scoped_lock_read_class"></a>  reader_writer_lock:: scoped_lock_read 類別

例外狀況安全 RAII 包裝函式，可用來取得`reader_writer_lock`讀者鎖定物件。

```
class scoped_lock_read;
```

##  <a name="try_lock"></a> try_lock

嘗試取得 reader-writer 鎖定為寫入器，而不會封鎖。

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read

建構`scoped_lock_read`物件，並取得`reader_writer_lock`傳入物件`_Reader_writer_lock`讀者的參數。 如果為寫入器的另一個執行緒的鎖定，或有暫止的寫入器，將會封鎖這個呼叫。

```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

#### <a name="parameters"></a>參數

*_Reader_writer_lock*<br/>
`reader_writer_lock`讀者所取得的物件。

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

如果已取得鎖定，值 **，則為 true**; 否則值**false**。

##  <a name="try_lock_read"></a> try_lock_read

嘗試取得讀者 reader-writer 鎖定，而不會封鎖。

```
bool try_lock_read();
```

### <a name="return-value"></a>傳回值

如果已取得鎖定，值 **，則為 true**; 否則值**false**。

##  <a name="unlock"></a> 解除鎖定

根據使用者鎖定，讀取器或寫入 reader-writer 鎖定會解除鎖定。

```
void unlock();
```

### <a name="remarks"></a>備註

如果寫入器鎖定上等候，鎖定的版本會一律會移至 FIFO 順序的下一個寫入器。 這個鎖定偏向寫入器，將會佔用連續載入寫入器在讀取器。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[critical_section 類別](critical-section-class.md)
