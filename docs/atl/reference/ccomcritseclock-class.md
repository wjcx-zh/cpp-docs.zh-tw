---
title: CComCritSecLock 類別
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: fd2904f67d84db42d6b35aa4e505b063d6ea9a9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224288"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 類別

這個類別會提供鎖定和解除鎖定重要區段物件的方法。

## <a name="syntax"></a>語法

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>參數

*TLock*<br/>
要鎖定和解除鎖定的物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|建構函式。|
|[CComCritSecLock：： ~ CComCritSecLock](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[CComCritSecLock：： Lock](#lock)|呼叫這個方法來鎖定重要區段物件。|
|[CComCritSecLock：： Unlock](#unlock)|呼叫這個方法來解除鎖定重要區段物件。|

## <a name="remarks"></a>備註

使用這個類別，以更安全的方式來鎖定和解除鎖定物件，而不是使用[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

建構函式。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>參數

*cs*<br/>
Critical 區段物件。

*bInitialLock*<br/>
初始鎖定狀態： **`true`** 表示已鎖定。

### <a name="remarks"></a>備註

初始化 critical 區段物件。

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock：： ~ CComCritSecLock

解構函式。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>備註

解除鎖定重要區段物件。

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock：： Lock

呼叫這個方法來鎖定重要區段物件。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

如果物件已成功鎖定，則會傳回 S_OK，否則會傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果物件已鎖定，則會在 debug build 中發生判斷提示錯誤。

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock：： Unlock

呼叫這個方法來解除鎖定重要區段物件。

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>備註

如果物件已解除鎖定，則會在 debug build 中發生 ASSERT 錯誤。

## <a name="see-also"></a>另請參閱

[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)
