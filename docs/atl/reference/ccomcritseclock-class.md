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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cb07c2cca9394c23c6c3db156e205749f62e3f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 類別
這個類別會提供用以鎖定及解除鎖定的關鍵區段物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>參數  
 *TLock*  
 要鎖定及解除鎖定的物件。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|建構函式。|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|呼叫此方法以鎖定的重要區段的物件。|  
|[CComCritSecLock::Unlock](#unlock)|呼叫這個方法來解除鎖定的重要區段的物件。|  
  
## <a name="remarks"></a>備註  
 使用這個類別來鎖定和解除鎖定的物件，以更安全方式比搭配[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="ctor"></a>CComCritSecLock::CComCritSecLock  
 建構函式。  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>參數  
 *cs*  
 重要區段的物件。  
  
 `bInitialLock`  
 初始鎖定狀態： **true**鎖定的方法。  
  
### <a name="remarks"></a>備註  
 初始化關鍵區段的物件。  
  
##  <a name="dtor"></a>CComCritSecLock:: ~ CComCritSecLock  
 解構函式。  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>備註  
 解除鎖定的重要區段的物件。  
  
##  <a name="lock"></a>CComCritSecLock::Lock  
 呼叫此方法以鎖定的重要區段的物件。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果物件已成功地鎖定或在失敗的 HRESULT 錯誤。  
  
### <a name="remarks"></a>備註  
 如果物件已鎖定，會在偵錯組建中發生判斷提示錯誤。  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 呼叫這個方法來解除鎖定的重要區段的物件。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>備註  
 如果物件已解除鎖定，會在偵錯組建中發生判斷提示錯誤。  
  
## <a name="see-also"></a>請參閱  
 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)
