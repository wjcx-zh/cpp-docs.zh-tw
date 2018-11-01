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
ms.openlocfilehash: 97b2f2f18687805f20999e9513977538390b0e37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543789"
---
# <a name="ccomapartment-class"></a>CComApartment 類別

這個類別會提供支援，來管理執行緒集區的 EXE 模組中的 apartment。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CComApartment
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|將標記執行緒的開始位址。|
|[CComApartment::GetLockCount](#getlockcount)|傳回執行緒的目前鎖定計數。|
|[CComApartment::Lock](#lock)|執行緒的鎖定計數遞增。|
|[CComApartment::Unlock](#unlock)|執行緒的鎖定計數遞減。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|包含執行緒的識別碼。|
|[CComApartment::m_hThread](#m_hthread)|包含執行緒的控制代碼。|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|包含執行緒的目前鎖定計數。|

## <a name="remarks"></a>備註

`CComApartment` 由[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)來管理執行緒集區的 EXE 模組中的 apartment。 `CComApartment` 提供方法來遞增及遞減鎖定計數在執行緒上。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="apartment"></a>  CComApartment::Apartment

將標記執行緒的開始位址。

```
DWORD Apartment();
```

### <a name="return-value"></a>傳回值

永遠為 0。

### <a name="remarks"></a>備註

自動設定期間[CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init)。

##  <a name="ccomapartment"></a>  CComApartment::CComApartment

建構函式。

```
CComApartment();
```

### <a name="remarks"></a>備註

初始化`CComApartment`資料成員[m_nLockCnt](#m_nlockcnt)並[m_hThread](#m_hthread)。

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

傳回執行緒的目前鎖定計數。

```
LONG GetLockCount();
```

### <a name="return-value"></a>傳回值

在執行緒上的鎖定計數。

##  <a name="lock"></a>  CComApartment::Lock

執行緒的鎖定計數遞增。

```
LONG Lock();
```

### <a name="return-value"></a>傳回值

值，這個值可能有助於診斷或測試。

### <a name="remarks"></a>備註

由呼叫[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)。

在執行緒上的鎖定計數用於統計用途。

##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID

包含執行緒的識別碼。

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>  CComApartment::m_hThread

包含執行緒的控制代碼。

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt

包含執行緒的目前鎖定計數。

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

執行緒的鎖定計數遞減。

```
LONG Unlock();
```

### <a name="return-value"></a>傳回值

值，這個值可能有助於診斷或測試。

### <a name="remarks"></a>備註

由呼叫[CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)。

在執行緒上的鎖定計數用於統計用途。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
