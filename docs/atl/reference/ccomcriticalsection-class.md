---
title: CComCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: 8cf590052dee9d0303ccfb102296fc66038aec57
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224301"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 類別

這個類別會提供方法來取得和釋放重要區段物件的擁有權。

## <a name="syntax"></a>語法

```
class CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComCriticalSection：： Init](#init)|建立並初始化重要區段物件。|
|[CComCriticalSection：： Lock](#lock)|取得重要區段物件的擁有權。|
|[CComCriticalSection：： Term](#term)|釋放 critical 區段物件所使用的系統資源。|
|[CComCriticalSection：： Unlock](#unlock)|釋放重要區段物件的擁有權。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CComCriticalSection：： m_sec](#m_sec)|CRITICAL_SECTION 物件。|

## <a name="remarks"></a>備註

`CComCriticalSection`類似于類別[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，不同之處在于您必須明確初始化並釋放重要區段。

一般來說，您會 `CComCriticalSection` 透過 **`typedef`** 名稱[CriticalSection](ccommultithreadmodel-class.md#criticalsection)來使用。 `CComCriticalSection`使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)時，會參考此名稱。

請參閱[CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)，以取得更安全的方式來使用此類別，而不是 `Lock` 直接呼叫和 `Unlock` 。

## <a name="requirements"></a>需求

**標頭：** atlcore。h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

建構函式。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>備註

將[m_sec](#m_sec)的資料成員設定為 Null。

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CComCriticalSection：： Init

呼叫 Win32 函數[InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)，它會初始化包含在[m_sec](#m_sec)資料成員中的重要區段物件。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

會在失敗時傳回成功、E_OUTOFMEMORY 或 E_FAIL 上的 S_OK。

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CComCriticalSection：： Lock

呼叫 Win32 函式[EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)，這會等到執行緒可以取得包含在[m_sec](#m_sec)資料成員中之重要區段物件的擁有權。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

會在失敗時傳回成功、E_OUTOFMEMORY 或 E_FAIL 上的 S_OK。

### <a name="remarks"></a>備註

必須先使用[Init](#init)方法的呼叫來初始化 critical 區段物件。 當受保護的程式碼完成執行時，執行緒必須呼叫[解除鎖定](#unlock)以釋放重要區段的擁有權。

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CComCriticalSection：： m_sec

包含所有方法所使用的重要區段物件 `CComCriticalSection` 。

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CComCriticalSection：： Term

呼叫 Win32 函式[DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)，此函式會釋放包含在[m_sec](#m_sec)資料成員中的重要區段物件所使用的所有資源。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

`Term`呼叫之後，重要區段就無法再用於同步處理。

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CComCriticalSection：： Unlock

呼叫 Win32 函式[LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)，此函式會釋放包含在[m_sec](#m_sec)資料成員中之重要區段物件的擁有權。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要先取得擁有權，執行緒必須呼叫[Lock](#lock)方法。 對於的每個呼叫都 `Lock` 需要相對應的呼叫， `Unlock` 才能釋放重要區段的擁有權。

## <a name="see-also"></a>另請參閱

[CComFakeCriticalSection 類別](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)
