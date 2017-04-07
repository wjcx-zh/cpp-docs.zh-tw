---
title: "CAutoRevertImpersonation 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: 22
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
ms.openlocfilehash: f86f1e5067583b3c4c615c8ca3095e8b67b3fffe
ms.lasthandoff: 02/24/2017

---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 類別
這個類別會還原[CAccessToken](../../atl/reference/caccesstoken-class.md) nonimpersonating 狀態時超出範圍的物件。  
  
## <a name="syntax"></a>語法  
  
```
class CAutoRevertImpersonation
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|建構`CAutoRevertImpersonation`物件|  
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|終結物件，並還原存取權杖模擬。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|會自動模擬回復的存取權杖。|  
|[CAutoRevertImpersonation::Detach](#detach)|取消自動模擬回復。|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|擷取這個物件相關聯的存取語彙基元目前。|  
  
## <a name="remarks"></a>備註  
 [存取權杖](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一個物件，描述處理序或執行緒的安全性內容，並配置給每位使用者登入 Windows NT 或 Windows 2000 的系統。 這些存取語彙基元可以用表示`CAccessToken`類別。  
  
 有時是必須模擬存取權杖。 提供這個類別是為了方便，但不會執行模擬的存取權杖。它只會執行自動回復為 nonimpersonated 的狀態。 這是因為權杖存取模擬可以執行數個不同的方式。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="attach"></a>CAutoRevertImpersonation::Attach  
 會自動模擬回復的存取權杖。  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>參數  
 `pAT`  
 位址[CAccessToken](../../atl/reference/caccesstoken-class.md)物件會自動還原  
  
### <a name="remarks"></a>備註  
 這個方法應該只用於如果[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)物件建立具有 NULL`CAccessToken`指標，或如果[卸離](#detach)先前呼叫。 簡單的情況下，不需要使用此方法。  
  
##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation  
 建構 `CAutoRevertImpersonation` 物件。  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>參數  
 `pAT`  
 位址[CAccessToken](../../atl/reference/caccesstoken-class.md)物件會自動還原。  
  
### <a name="remarks"></a>備註  
 從，最好是在建立之前的存取權杖的實際模擬也應該分別執行`CAutoRevertImpersonation`物件。 這種模擬將會自動還原時`CAutoRevertImpersonation`物件超出範圍。  
  
##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 終結物件，並還原存取權杖模擬。  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>備註  
 還原作用中的任何目前的模擬[CAccessToken](../../atl/reference/caccesstoken-class.md)物件在建構或透過提供[附加](#attach)方法。 如果沒有`CAccessToken`是解構函式相關聯的沒有任何作用。  
  
##  <a name="detach"></a>CAutoRevertImpersonation::Detach  
 取消自動模擬回復。  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 先前相關聯的位址[CAccessToken](../../atl/reference/caccesstoken-class.md)，或如果不存在則為 NULL。  
  
### <a name="remarks"></a>備註  
 呼叫**卸離**防止`CAutoRevertImpersonation`從還原的任何模擬目前作用中的物件[CAccessToken](../../atl/reference/caccesstoken-class.md)與此物件相關聯的物件。 `CAutoRevertImpersonation`然後可以終結時不會影響或在重新關聯到相同或另一個`CAccessToken`物件使用[附加](#attach)。  
  
##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken  
 擷取這個物件相關聯的存取語彙基元目前。  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>傳回值  
 先前相關聯的位址[CAccessToken](../../atl/reference/caccesstoken-class.md)，或如果不存在則為 NULL。  
  
### <a name="remarks"></a>備註  
 如果此方法稱為基於包含模擬的回復`CAccessToken`物件，[卸離](#detach)應該改為使用方法。  
  
## <a name="see-also"></a>另請參閱  
 [ATLSecurity 範例](../../visual-cpp-samples.md)   
 [存取權杖](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [類別概觀](../../atl/atl-class-overview.md)

