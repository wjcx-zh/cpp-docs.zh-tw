---
title: "CComCritSecLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 71b9ab8b11adc946656c2192c2f0f06555ef1254
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 類別
這個類別會提供用以鎖定及解除鎖定重要區段物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>參數  
 *TLock*  
 要鎖定和解除鎖定的物件。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|建構函式。|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|呼叫此方法以鎖定重要區段物件。|  
|[CComCritSecLock::Unlock](#unlock)|呼叫這個方法來解除鎖定重要區段物件。|  
  
## <a name="remarks"></a>備註  
 使用這個類別來鎖定和解除鎖定的物件，以更安全的方式比在[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="ctor"></a>CComCritSecLock::CComCritSecLock  
 建構函式。  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>參數  
 *cs*  
 重要區段物件。  
  
 `bInitialLock`  
 初始鎖定狀態︰ **true**鎖定的方式。  
  
### <a name="remarks"></a>備註  
 重要區段物件初始化。  
  
##  <a name="dtor"></a>CComCritSecLock:: ~ CComCritSecLock  
 解構函式。  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>備註  
 解除鎖定重要區段物件。  
  
##  <a name="lock"></a>CComCritSecLock::Lock  
 呼叫此方法以鎖定重要區段物件。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果物件已成功鎖定或在失敗的 HRESULT 錯誤。  
  
### <a name="remarks"></a>備註  
 如果物件已鎖定，判斷提示錯誤會發生在偵錯組建。  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 呼叫這個方法來解除鎖定重要區段物件。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>備註  
 如果物件已解除鎖定，會在偵錯組建中發生判斷提示錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)

