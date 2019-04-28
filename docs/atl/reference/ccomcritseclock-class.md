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
ms.openlocfilehash: 045e64504707fa8978c8236b376037d9f57bf12c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259803"
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

|名稱|描述|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|建構函式。|
|[CComCritSecLock::~CComCritSecLock](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|呼叫這個方法來鎖定重要區段物件。|
|[CComCritSecLock::Unlock](#unlock)|呼叫這個方法來解除鎖定重要區段物件。|

## <a name="remarks"></a>備註

使用這個類別來鎖定和解除鎖定物件，比使用更安全的方式[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)或是[CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

建構函式。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>參數

*cs*<br/>
重要區段物件。

*bInitialLock*<br/>
初始鎖定狀態： **，則為 true**鎖定的方法。

### <a name="remarks"></a>備註

重要區段物件初始化。

##  <a name="dtor"></a>  CComCritSecLock:: ~ CComCritSecLock

解構函式。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>備註

解除鎖定重要區段物件。

##  <a name="lock"></a>  CComCritSecLock::Lock

呼叫這個方法來鎖定重要區段物件。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

在失敗時傳回 S_OK，如果已成功鎖定的物件或錯誤的 HRESULT。

### <a name="remarks"></a>備註

如果物件已鎖定，會在偵錯組建中發生判斷提示錯誤。

##  <a name="unlock"></a>  CComCritSecLock::Unlock

呼叫這個方法來解除鎖定重要區段物件。

```
void Unlock() throw();
```

### <a name="remarks"></a>備註

如果物件已經解除鎖定，會在偵錯組建中發生判斷提示錯誤。

## <a name="see-also"></a>另請參閱

[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)
