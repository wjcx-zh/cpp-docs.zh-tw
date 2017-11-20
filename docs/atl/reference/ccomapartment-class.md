---
title: "CComApartment 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a7e7fce463e7aabe6b27cb9e5fb3dbb36fd8983
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ccomapartment-class"></a>CComApartment 類別
這個類別會提供用於管理執行緒集區的 EXE 模組中 appartment 支援。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComApartment
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|將標示執行緒的起始位址。|  
|[CComApartment::GetLockCount](#getlockcount)|傳回執行緒的目前鎖定計數。|  
|[CComApartment::Lock](#lock)|執行緒的鎖定計數遞增。|  
|[CComApartment::Unlock](#unlock)|執行緒的鎖定計數遞減。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|包含執行緒的識別項。|  
|[CComApartment::m_hThread](#m_hthread)|包含執行緒的處理常式。|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|包含執行緒的目前鎖定計數。|  
  
## <a name="remarks"></a>備註  
 `CComApartment`正由[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)管理 apartment 執行緒集區的 EXE 模組中。 `CComApartment`提供執行緒計數遞增和遞減鎖定的方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="apartment"></a>CComApartment::Apartment  
 將標示執行緒的起始位址。  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>傳回值  
 永遠為 0。  
  
### <a name="remarks"></a>備註  
 自動設定期間[CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init)。  
  
##  <a name="ccomapartment"></a>CComApartment::CComApartment  
 建構函式。  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>備註  
 初始化`CComApartment`資料成員[m_nLockCnt](#m_nlockcnt)和[m_hThread](#m_hthread)。  
  
##  <a name="getlockcount"></a>CComApartment::GetLockCount  
 傳回執行緒的目前鎖定計數。  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>傳回值  
 在執行緒上的鎖定計數。  
  
##  <a name="lock"></a>CComApartment::Lock  
 執行緒的鎖定計數遞增。  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
### <a name="remarks"></a>備註  
 由呼叫[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)。  
  
 在執行緒上的鎖定計數是基於統計目的使用。  
  
##  <a name="m_dwthreadid"></a>CComApartment::m_dwThreadID  
 包含執行緒的識別項。  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="m_hthread"></a>CComApartment::m_hThread  
 包含執行緒的處理常式。  
  
```
HANDLE m_hThread;
```  
  
##  <a name="m_nlockcnt"></a>CComApartment::m_nLockCnt  
 包含執行緒的目前鎖定計數。  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="unlock"></a>CComApartment::Unlock  
 執行緒的鎖定計數遞減。  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
### <a name="remarks"></a>備註  
 由呼叫[CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)。  
  
 在執行緒上的鎖定計數是基於統計目的使用。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
