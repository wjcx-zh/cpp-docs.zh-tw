---
title: critical_section 類別
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: a08cb5049d742a9740361595bd931a2f7a48bd16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498758"
---
# <a name="criticalsection-class"></a>critical_section 類別

其為並行執行階段明確察覺且不可重新進入的 Mutex。

## <a name="syntax"></a>語法

```
class critical_section;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`native_handle_type`|對 `critical_section` 物件的參考。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[critical_section:: scoped_lock 類別](#critical_section__scoped_lock_class)|例外狀況安全 RAII 包裝函式`critical_section`物件。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[critical_section](#ctor)|建構新的重要區段。|
|[~ critical_section 解構函式](#dtor)|終結重要區段。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[lock](#lock)|取得這個重要的區段。|
|[native_handle](#native_handle)|如果有的話，會傳回平台特定原生控制代碼。|
|[try_lock](#try_lock)|嘗試取得鎖定，而不會封鎖。|
|[try_lock_for](#try_lock_for)|嘗試取得鎖定，而不進行特定毫秒數的封鎖。|
|[unlock](#unlock)|解除鎖定重要區段。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`critical_section`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> critical_section

建構新的重要區段。

```
critical_section();
```

##  <a name="dtor"></a> ~critical_section

終結重要區段。

```
~critical_section();
```

### <a name="remarks"></a>備註

預期的是解構函式執行時，不會再保留鎖定。 允許重要區段，來解構的鎖定仍保留在未定義的行為結果。

##  <a name="lock"></a> 鎖定

取得這個重要的區段。

```
void lock();
```

### <a name="remarks"></a>備註

通常是安全的作法是利用[scoped_lock](#critical_section__scoped_lock_class)建構函式來取得和釋放`critical_section`物件中發生例外狀況安全的方式。

如果所呼叫的內容中，已進行鎖定[improper_lock](improper-lock-class.md)會擲回例外狀況。

##  <a name="native_handle"></a> native_handle

如果有的話，會傳回平台特定原生控制代碼。

```
native_handle_type native_handle();
```

### <a name="return-value"></a>傳回值

重要區段的參考。

### <a name="remarks"></a>備註

A`critical_section`物件不是 Windows 作業系統的平台特定原生控制代碼相關聯。 此方法只會傳回物件本身的參考。

##  <a name="critical_section__scoped_lock_class"></a>  critical_section:: scoped_lock 類別

例外狀況安全 RAII 包裝函式`critical_section`物件。

```
class scoped_lock;
```

##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock

建構`scoped_lock`物件，並取得`critical_section`傳入物件`_Critical_section`參數。 如果由另一個執行緒持有重要區段，將會封鎖這個呼叫。

```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>參數

*_Critical_section*<br/>
若要鎖定重要區段。

##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

終結`scoped_lock`物件，並釋放其建構函式中所提供的重要區段。

```
~scoped_lock();
```

##  <a name="try_lock"></a> try_lock

嘗試取得鎖定，而不會封鎖。

```
bool try_lock();
```

### <a name="return-value"></a>傳回值

如果已取得鎖定，值 **，則為 true**; 否則值**false**。

##  <a name="try_lock_for"></a> try_lock_for

嘗試取得鎖定，而不進行特定毫秒數的封鎖。

```
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>參數

*逾時 _t*<br/>
在逾時前要等候的毫秒數。

### <a name="return-value"></a>傳回值

如果已取得鎖定，值 **，則為 true**; 否則值**false**。

##  <a name="unlock"></a> 解除鎖定

解除鎖定重要區段。

```
void unlock();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[reader_writer_lock 類別](reader-writer-lock-class.md)
