---
title: CComCriticalSection 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f6009af2026f10ff25983544e6724385246a42f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755740"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 類別

這個類別提供方法來取得和釋放重要區段物件的擁有權。

## <a name="syntax"></a>語法

```
class CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|建立並初始化重要區段物件。|
|[CComCriticalSection::Lock](#lock)|取得重要區段物件的擁有權。|
|[CComCriticalSection::Term](#term)|釋放重要區段物件所使用的系統資源。|
|[CComCriticalSection::Unlock](#unlock)|釋放重要區段物件的擁有權。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|CRITICAL_SECTION 物件。|

## <a name="remarks"></a>備註

`CComCriticalSection` 類似於類別[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，只不過您必須明確地初始化，並釋放重要區段。

一般而言，您可以使用`CComCriticalSection`經由**typedef**名稱[CriticalSection](ccommultithreadmodel-class.md#criticalsection)。 此名稱會參考`CComCriticalSection`時[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。  

請參閱[CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)有更安全的方法，可使用比呼叫這個類別`Lock`和`Unlock`直接。

## <a name="requirements"></a>需求

**標頭：** atlcore.h

##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection

建構函式。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>備註

設定組[m_sec](#m_sec)為 NULL 的資料成員。

##  <a name="init"></a>  CComCriticalSection::Init

呼叫 Win32 函式[InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection)，這會初始化中包含的重要區段物件[m_sec](#m_sec)資料成員。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

成功時，E_OUTOFMEMORY 或 E_FAIL，在失敗時傳回 S_OK。

##  <a name="lock"></a>  CComCriticalSection::Lock

呼叫 Win32 函式[EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection)，哪一個等候，直到執行緒可以取得所含的重要區段物件的擁有權[m_sec](#m_sec)資料成員。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

成功時，E_OUTOFMEMORY 或 E_FAIL，在失敗時傳回 S_OK。

### <a name="remarks"></a>備註

重要區段物件必須先呼叫初始化[Init](#init)方法。 當受保護的程式碼完成執行時，必須呼叫執行緒[Unlock](#unlock)釋放重要區段的擁有權。

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

包含所有使用的重要區段物件`CComCriticalSection`方法。

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>  CComCriticalSection::Term

呼叫 Win32 函式[DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection)，其中包含在重要區段物件所使用的資源全部釋出[m_sec](#m_sec)資料成員。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

一次`Term`已呼叫的重要區段不可以用於同步處理。

##  <a name="unlock"></a>  CComCriticalSection::Unlock

呼叫 Win32 函式[LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection)，這會釋放所含的重要區段物件的擁有權[m_sec](#m_sec)資料成員。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要先取得擁有權，必須呼叫的執行緒[鎖定](#lock)方法。 每次呼叫`Lock`需要對應呼叫`Unlock`釋放重要區段的擁有權。

## <a name="see-also"></a>另請參閱

[CComFakeCriticalSection 類別](../../atl/reference/ccomfakecriticalsection-class.md)   
[類別概觀](../../atl/atl-class-overview.md)   
[CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)
