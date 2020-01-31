---
title: CComApartment 類別
ms.date: 11/04/2016
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 5f4c7fc356e61210e9b99bf9989b1bb3f0abc98a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821671"
---
# <a name="ccomapartment-class"></a>CComApartment 類別

此類別提供線上程集區 EXE 模組中管理單元的支援。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComApartment
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|建構函式。|

### <a name="public-methods"></a>公用方法

|Name|描述|
|----------|-----------------|
|[CComApartment：：公寓](#apartment)|標記執行緒的起始位址。|
|[CComApartment::GetLockCount](#getlockcount)|傳回執行緒目前的鎖定計數。|
|[CComApartment：： Lock](#lock)|遞增執行緒的鎖定計數。|
|[CComApartment：： Unlock](#unlock)|遞減執行緒的鎖定計數。|

### <a name="public-data-members"></a>公用資料成員

|Name|描述|
|----------|-----------------|
|[CComApartment：： m_dwThreadID](#m_dwthreadid)|包含執行緒的識別碼。|
|[CComApartment：： m_hThread](#m_hthread)|包含執行緒的控制碼。|
|[CComApartment：： m_nLockCnt](#m_nlockcnt)|包含執行緒目前的鎖定計數。|

## <a name="remarks"></a>備註

[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)會使用 `CComApartment` 來管理執行緒集區 EXE 模組中的公寓。 `CComApartment` 提供線上程上遞增和遞減鎖定計數的方法。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="apartment"></a>CComApartment：：公寓

標記執行緒的起始位址。

```
DWORD Apartment();
```

### <a name="return-value"></a>傳回值

一律為0。

### <a name="remarks"></a>備註

在[CComAutoThreadModule：： Init](../../atl/reference/ccomautothreadmodule-class.md#init)期間自動設定。

##  <a name="ccomapartment"></a>CComApartment::CComApartment

建構函式。

```
CComApartment();
```

### <a name="remarks"></a>備註

將 `CComApartment` 的資料成員初始化[m_nLockCnt](#m_nlockcnt)和[m_hThread](#m_hthread)。

##  <a name="getlockcount"></a>CComApartment::GetLockCount

傳回執行緒目前的鎖定計數。

```
LONG GetLockCount();
```

### <a name="return-value"></a>傳回值

執行緒上的鎖定計數。

##  <a name="lock"></a>CComApartment：： Lock

遞增執行緒的鎖定計數。

```
LONG Lock();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

### <a name="remarks"></a>備註

由[CComAutoThreadModule：： Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)呼叫。

執行緒上的鎖定計數用於統計用途。

##  <a name="m_dwthreadid"></a>CComApartment：： m_dwThreadID

包含執行緒的識別碼。

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>CComApartment：： m_hThread

包含執行緒的控制碼。

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>CComApartment：： m_nLockCnt

包含執行緒目前的鎖定計數。

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>CComApartment：： Unlock

遞減執行緒的鎖定計數。

```
LONG Unlock();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

### <a name="remarks"></a>備註

由[CComAutoThreadModule：： Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)呼叫。

執行緒上的鎖定計數用於統計用途。

## <a name="see-also"></a>請參閱

[類別總覽](../../atl/atl-class-overview.md)
