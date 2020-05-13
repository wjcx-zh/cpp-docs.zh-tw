---
title: CCom公寓類別
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
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321110"
---
# <a name="ccomapartment-class"></a>CCom公寓類別

此類支援在線程池 EXE 模組中管理單元。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComApartment
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom公寓:CCom公寓](#ccomapartment)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom公寓:公寓](#apartment)|標記線程的起始位址。|
|[CCom公寓::獲取鎖計數](#getlockcount)|返回線程的當前鎖計數。|
|[CCom公寓:鎖](#lock)|增加線程的鎖計數。|
|[CCom公寓:解鎖](#unlock)|撤銷線程的鎖計數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCom公寓:m_dwThreadID](#m_dwthreadid)|包含線程的標識碼。|
|[CCom公寓:m_hThread](#m_hthread)|包含線程的句柄。|
|[CCom公寓:m_nLockCnt](#m_nlockcnt)|包含線程的當前鎖計數。|

## <a name="remarks"></a>備註

`CComApartment`[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)用於管理線程池 EXE 模組中的單元。 `CComApartment`提供了在線程上增加和遞減鎖計數的方法。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CCom公寓:公寓

標記線程的起始位址。

```
DWORD Apartment();
```

### <a name="return-value"></a>傳回值

一律是 0。

### <a name="remarks"></a>備註

[在 CComautoThread 模組期間自動設定::init](../../atl/reference/ccomautothreadmodule-class.md#init)。

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CCom公寓:CCom公寓

建構函式。

```
CComApartment();
```

### <a name="remarks"></a>備註

初始化`CComApartment`資料成員[m_nLockCnt](#m_nlockcnt)和[m_hThread。](#m_hthread)

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CCom公寓::獲取鎖計數

返回線程的當前鎖計數。

```
LONG GetLockCount();
```

### <a name="return-value"></a>傳回值

線程上的鎖計數。

## <a name="ccomapartmentlock"></a><a name="lock"></a>CCom公寓:鎖

增加線程的鎖計數。

```
LONG Lock();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

### <a name="remarks"></a>備註

由[CComAutoThreadModule 呼叫鎖定](../../atl/reference/ccomautothreadmodule-class.md#lock)。

線程上的鎖計數用於統計目的。

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CCom公寓:m_dwThreadID

包含線程的標識碼。

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CCom公寓:m_hThread

包含線程的句柄。

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CCom公寓:m_nLockCnt

包含線程的當前鎖計數。

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CCom公寓:解鎖

撤銷線程的鎖計數。

```
LONG Unlock();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

### <a name="remarks"></a>備註

由[CComAutoThreadModule 呼叫:解鎖](../../atl/reference/ccomautothreadmodule-class.md#lock)。

線程上的鎖計數用於統計目的。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
