---
title: "CComCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 827ba99a141799af42fab65c36df1f22d212260a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 類別
這個類別會提供方法來取得及釋放重要區段物件的擁有權。  
  
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
|[CComCriticalSection::Init](#init)|建立並初始化的關鍵區段物件。|  
|[CComCriticalSection::Lock](#lock)|取得重要區段物件的擁有權。|  
|[CComCriticalSection::Term](#term)|釋放重要區段物件所使用的系統資源。|  
|[CComCriticalSection::Unlock](#unlock)|釋放重要區段物件的擁有權。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|A **CRITICAL_SECTION**物件。|  
  
## <a name="remarks"></a>備註  
 `CComCriticalSection`類似於類別[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，只不過您必須明確地初始化，並釋放重要區段。  
  
 通常，您會使用`CComCriticalSection`透過`typedef`名稱[CriticalSection](ccommultithreadmodel-class.md#criticalsection)。 此名稱參考`CComCriticalSection`時[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。  

  
 請參閱[CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)的一個更安全的方式來使用這個類別，比呼叫`Lock`和`Unlock`直接。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection  
 建構函式。  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>備註  
 設定[m_sec](#m_sec)為 NULL 的資料成員**。**  
  
##  <a name="init"></a>CComCriticalSection::Init  
 呼叫 Win32 函式[InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472)，其中初始化中包含的關鍵區段物件[m_sec](#m_sec)資料成員。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`成功時， **E_OUTOFMEMORY**或**E_FAIL**失敗。  
  
##  <a name="lock"></a>CComCriticalSection::Lock  
 呼叫 Win32 函式[EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608)，直到執行緒可以取得包含在關鍵區段物件的擁有權的等候[m_sec](#m_sec)資料成員。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`成功時， **E_OUTOFMEMORY**或**E_FAIL**失敗。  
  
### <a name="remarks"></a>備註  
 關鍵區段物件必須先呼叫初始化[Init](#init)方法。 當受保護的程式碼完成執行時，必須呼叫執行緒[Unlock](#unlock)釋關鍵區段的擁有權。  
  
##  <a name="m_sec"></a>CComCriticalSection::m_sec  
 包含可由所有的關鍵區段物件`CComCriticalSection`方法。  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>CComCriticalSection::Term  
 呼叫 Win32 函式[DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552)，其中包含在關鍵區段物件所使用的資源全部釋出[m_sec](#m_sec)資料成員。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 一次`Term`呼叫之後的重要區段不會再用於進行同步處理。  
  
##  <a name="unlock"></a>CComCriticalSection::Unlock  
 呼叫 Win32 函式[LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169)，其中所含的關鍵區段物件的擁有權釋放[m_sec](#m_sec)資料成員。  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要先取得擁有權，必須呼叫執行緒[鎖定](#lock)方法。 每次呼叫`Lock`需要對應呼叫`Unlock`釋關鍵區段的擁有權。  
  
## <a name="see-also"></a>請參閱  
 [CComFakeCriticalSection 類別](../../atl/reference/ccomfakecriticalsection-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)
