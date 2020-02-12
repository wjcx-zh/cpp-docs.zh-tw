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
ms.openlocfilehash: 1a7386e527b5327d928bfdcb3281c88666f1b106
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140856"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock 類別

以寫入器偏好設定佇列為基礎且只能本機微調的讀取器-寫入器鎖定。 鎖定會授與寫入器先進先出 (FIFO) 存取權，並在連續載入寫入器的情況下影響讀取器。

## <a name="syntax"></a>語法

```cpp
class reader_writer_lock;
```

## <a name="members"></a>成員

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[reader_writer_lock：： scoped_lock 類別](#scoped_lock_class)|例外狀況安全的 RAII 包裝函式，可用來取得 `reader_writer_lock` 鎖定物件做為寫入器。|
|[reader_writer_lock：： scoped_lock_read 類別](#scoped_lock_read_class)|例外狀況安全的 RAII 包裝函式，可用來取得 `reader_writer_lock` 鎖定物件做為讀取器。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[reader_writer_lock](#ctor)|建構新的 `reader_writer_lock` 物件。|
|[~ reader_writer_lock 的析構函式](#dtor)|終結 `reader_writer_lock` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[lock](#lock)|取得讀取器寫入器鎖定做為寫入器。|
|[lock_read](#lock_read)|取得讀取器寫入器鎖定做為讀取器。 如果有寫入器，則作用中的讀取者必須等到完成作業。 讀取器只會在鎖定中註冊感興趣，並等候寫入器釋放它。|
|[try_lock](#try_lock)|嘗試取得讀取器寫入器鎖定做為寫入器，而不封鎖。|
|[try_lock_read](#try_lock_read)|嘗試取得讀取器寫入器鎖定做為讀取器，而不封鎖。|
|[unlock](#unlock)|根據鎖定的物件、讀取器或寫入器，解除鎖定讀取者寫入器鎖定。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`reader_writer_lock`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="lock"></a>狀

取得讀取器寫入器鎖定做為寫入器。

```cpp
void lock();
```

### <a name="remarks"></a>備註

使用[scoped_lock](#scoped_lock_class)結構通常會更安全地以例外狀況安全的方式取得和釋放 `reader_writer_lock` 物件做為寫入器。

寫入器嘗試取得鎖定後，後續任何讀取器都會封鎖，直到寫入器成功取得及釋放鎖定為止。 這項鎖定會偏離寫入器，而且可以在寫入器的連續載入下使讀取者。

寫入器是連結的，因此，讀取者結束鎖定會在行中釋放下一個寫入器。

如果呼叫內容已持有鎖定，就會擲回[improper_lock](improper-lock-class.md)例外狀況。

## <a name="lock_read"></a>lock_read

取得讀取器寫入器鎖定做為讀取器。 如果有寫入器，則作用中的讀取者必須等到完成作業。 讀取器只會在鎖定中註冊感興趣，並等候寫入器釋放它。

```cpp
void lock_read();
```

### <a name="remarks"></a>備註

使用[scoped_lock_read](#scoped_lock_read_class)結構通常會更安全地以例外狀況安全的方式取得和釋放 `reader_writer_lock` 物件做為讀取器。

如果有寫入器正在等候鎖定，則讀取器會等候，直到行中的所有寫入器都已取得並釋放鎖定為止。 這項鎖定會偏離寫入器，而且可以在寫入器的連續載入下使讀取者。

## <a name="ctor"></a>reader_writer_lock

建構新的 `reader_writer_lock` 物件。

```cpp
reader_writer_lock();
```

## <a name="dtor"></a>~ reader_writer_lock

終結 `reader_writer_lock` 物件。

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>備註

在執行函式時，預期不會再保留鎖定。 在仍保留鎖定的情況允許讀取器寫入器鎖定時，會導致未定義的行為。

## <a name="scoped_lock_class"></a>reader_writer_lock：： scoped_lock 類別

例外狀況安全的 RAII 包裝函式，可用來取得 `reader_writer_lock` 鎖定物件做為寫入器。

```cpp
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a>scoped_lock：： scoped_lock

建立 `scoped_lock` 物件，並取得當做寫入器傳入 `_Reader_writer_lock` 參數中的 `reader_writer_lock` 物件。 如果鎖定由另一個執行緒持有，此呼叫將會封鎖。

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>參數

*_Reader_writer_lock*<br/>
要取得做為寫入器的 `reader_writer_lock` 物件。

## <a name="scoped_lock_dtor"></a>scoped_lock：： ~ scoped_lock

終結 `reader_writer_lock` 物件，並釋放其函式中提供的鎖定。

```cpp
~scoped_lock();
```

## <a name="scoped_lock_read_class"></a>reader_writer_lock：： scoped_lock_read 類別

例外狀況安全的 RAII 包裝函式，可用來取得 `reader_writer_lock` 鎖定物件做為讀取器。

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read：： scoped_lock_read

建立 `scoped_lock_read` 物件，並取得當做讀取器傳入 `_Reader_writer_lock` 參數中的 `reader_writer_lock` 物件。 如果鎖定由另一個執行緒做為寫入器持有，或有擱置的寫入器，此呼叫將會封鎖。

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>參數

*_Reader_writer_lock*<br/>
要取得做為讀取器的 `reader_writer_lock` 物件。

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor"> reader_writer_lock：： scoped_lock_read：： ~ scoped_lock_read 的析構函式

終結 `scoped_lock_read` 物件，並釋放其函式中提供的鎖定。

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a>try_lock

嘗試取得讀取器寫入器鎖定做為寫入器，而不封鎖。

### <a name="syntax"></a>語法

```cpp
bool try_lock();
```

### <a name="return-value"></a>傳回值

如果已取得鎖定，則值為**true**;否則，值**為 false**。

## <a name="try_lock_read"></a>try_lock_read

嘗試取得讀取器寫入器鎖定做為讀取器，而不封鎖。

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>傳回值

如果已取得鎖定，則值為**true**;否則，值**為 false**。

## <a name="unlock"></a>解除鎖定

根據鎖定的物件、讀取器或寫入器，解除鎖定讀取者寫入器鎖定。

```cpp
void unlock();
```

### <a name="remarks"></a>備註

如果有寫入器正在等候鎖定，鎖定的版本一律會以 FIFO 順序移到下一個寫入器。 這項鎖定會偏離寫入器，而且可以在寫入器的連續載入下使讀取者。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[critical_section 類別](critical-section-class.md)
