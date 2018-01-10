---
title: "CComFakeCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs: C++
helpviewer_keywords: CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b9f7b3b56193100d21ef7aebaba0ab6d9ecfd5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 類別
這個類別會提供相同的方法， [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)但並不會提供重要區段。  
  
## <a name="syntax"></a>語法  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|沒有任何作用，因為沒有任何重要的區段。|  
|[CComFakeCriticalSection::Lock](#lock)|沒有任何作用，因為沒有任何重要的區段。|  
|[CComFakeCriticalSection::Term](#term)|沒有任何作用，因為沒有任何重要的區段。|  
|[CComFakeCriticalSection::Unlock](#unlock)|沒有任何作用，因為沒有任何重要的區段。|  
  
## <a name="remarks"></a>備註  
 `CComFakeCriticalSection`反映的方法中找到[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 不過，`CComFakeCriticalSection`不提供重要的區段中; 因此，其方法不執行任何動作。  
  
 通常，您會使用`CComFakeCriticalSection`透過`typedef`命名時，可能是`AutoCriticalSection`或`CriticalSection`。 當使用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這兩種`typedef`名稱參考`CComFakeCriticalSection`。 當使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，其參考[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`分別。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
##  <a name="init"></a>CComFakeCriticalSection::Init  
 沒有任何作用，因為沒有任何重要的區段。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
##  <a name="lock"></a>CComFakeCriticalSection::Lock  
 沒有任何作用，因為沒有任何重要的區段。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
##  <a name="term"></a>CComFakeCriticalSection::Term  
 沒有任何作用，因為沒有任何重要的區段。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
##  <a name="unlock"></a>CComFakeCriticalSection::Unlock  
 沒有任何作用，因為沒有任何重要的區段。  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
