---
title: "CComApartment 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComApartment
- CComApartment
- ATL.CComApartment
dev_langs:
- C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 9359e2ab8c4a84ab66441e3eb8cfd39520fd4e8d
ms.lasthandoff: 02/24/2017

---
# <a name="ccomapartment-class"></a>CComApartment 類別
這個類別提供支援管理 apartment 執行緒集區的 EXE 模組中。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComApartment
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|標記的執行緒起始位址。|  
|[CComApartment::GetLockCount](#getlockcount)|傳回的執行緒目前的鎖定計數。|  
|[CComApartment::Lock](#lock)|執行緒的鎖定計數遞增。|  
|[CComApartment::Unlock](#unlock)|執行緒的鎖定計數遞減。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|包含執行緒的識別項。|  
|[CComApartment::m_hThread](#m_hthread)|包含執行緒的處理常式。|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|包含執行緒的目前鎖定計數。|  
  
## <a name="remarks"></a>備註  
 `CComApartment`使用[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)管理 apartment 執行緒集區的 EXE 模組中。 `CComApartment`提供方法來遞增和遞減鎖定計數的執行緒上。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameapartmenta--ccomapartmentapartment"></a><a name="apartment"></a>CComApartment::Apartment  
 標記的執行緒起始位址。  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>傳回值  
 永遠為 0。  
  
### <a name="remarks"></a>備註  
 期間自動設定[CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init)。  
  
##  <a name="a-nameccomapartmenta--ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CComApartment::CComApartment  
 建構函式。  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>備註  
 初始化`CComApartment`資料成員[m_nLockCnt](#m_nlockcnt)和[m_hThread](#m_hthread)。  
  
##  <a name="a-namegetlockcounta--ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CComApartment::GetLockCount  
 傳回的執行緒目前的鎖定計數。  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>傳回值  
 在執行緒上的鎖定計數。  
  
##  <a name="a-namelocka--ccomapartmentlock"></a><a name="lock"></a>CComApartment::Lock  
 執行緒的鎖定計數遞增。  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
### <a name="remarks"></a>備註  
 由呼叫[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)。  
  
 在執行緒上的鎖定計數用於統計用途。  
  
##  <a name="a-namemdwthreadida--ccomapartmentmdwthreadid"></a><a name="m_dwthreadid"></a>CComApartment::m_dwThreadID  
 包含執行緒的識別項。  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="a-namemhthreada--ccomapartmentmhthread"></a><a name="m_hthread"></a>CComApartment::m_hThread  
 包含執行緒的處理常式。  
  
```
HANDLE m_hThread;
```  
  
##  <a name="a-namemnlockcnta--ccomapartmentmnlockcnt"></a><a name="m_nlockcnt"></a>CComApartment::m_nLockCnt  
 包含執行緒的目前鎖定計數。  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="a-nameunlocka--ccomapartmentunlock"></a><a name="unlock"></a>CComApartment::Unlock  
 執行緒的鎖定計數遞減。  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
### <a name="remarks"></a>備註  
 由呼叫[CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)。  
  
 在執行緒上的鎖定計數用於統計用途。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

