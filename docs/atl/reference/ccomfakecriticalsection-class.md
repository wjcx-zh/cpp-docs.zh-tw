---
title: "CComFakeCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: 19
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
ms.openlocfilehash: 2c1269288e03a8ac9f359dad9acf1a81ddbc84c2
ms.lasthandoff: 02/24/2017

---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 類別
這個類別會提供與相同的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ，但不提供關鍵區段。  
  
## <a name="syntax"></a>語法  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|沒有什麼作用，因為沒有任何重要區段。|  
|[CComFakeCriticalSection::Lock](#lock)|沒有什麼作用，因為沒有任何重要區段。|  
|[CComFakeCriticalSection::Term](#term)|沒有什麼作用，因為沒有任何重要區段。|  
|[CComFakeCriticalSection::Unlock](#unlock)|沒有什麼作用，因為沒有任何重要區段。|  
  
## <a name="remarks"></a>備註  
 `CComFakeCriticalSection`鏡像中找到的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 不過，`CComFakeCriticalSection`不提供關鍵區段; 因此，它的方法不執行任何動作。  
  
 您通常會使用`CComFakeCriticalSection`透過`typedef`名稱，或是`AutoCriticalSection`或`CriticalSection`。 當使用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這兩種`typedef`名稱參考`CComFakeCriticalSection`。 當使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，它們會參考[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`分別。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcore.h  
  
##  <a name="init"></a>CComFakeCriticalSection::Init  
 沒有什麼作用，因為沒有任何重要區段。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
##  <a name="lock"></a>CComFakeCriticalSection::Lock  
 沒有什麼作用，因為沒有任何重要區段。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
##  <a name="term"></a>CComFakeCriticalSection::Term  
 沒有什麼作用，因為沒有任何重要區段。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
##  <a name="unlock"></a>CComFakeCriticalSection::Unlock  
 沒有什麼作用，因為沒有任何重要區段。  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

