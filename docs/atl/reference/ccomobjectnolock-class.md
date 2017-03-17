---
title: "CComObjectNoLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4cf4cad1a3b1a4ac0a21ef76a0eaca35732abf3a
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 類別
這個類別會實作**IUnknown**的非彙總的物件，但是不會遞增建構函式中的模組鎖定計數。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|建構函式。|  
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|在物件上的參考計數遞增。|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|傳回所要求介面的指標。|  
|[CComObjectNoLock::Release](#release)|遞減參考計數物件。|  
  
## <a name="remarks"></a>備註  
 `CComObjectNoLock`類似於[CComObject](../../atl/reference/ccomobject-class.md) ，因為它會實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)非彙總的物件; 不過，`CComObjectNoLock`中建構函式會遞增模組鎖定計數。  
  
 使用 ATL`CComObjectNoLock`內部的 class factory。 一般情況下，您不會直接使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="addref"></a>CComObjectNoLock::AddRef  
 在物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock  
 建構函式。 不同於[CComObject](../../atl/reference/ccomobject-class.md)，不會增加模組鎖定計數。  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>參數  
 **void\***  
 [in]不使用這個未命名的參數。 它有與其他對稱**CCom***XXX*`Object`*XXX*建構函式。  
  
##  <a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock  
 解構函式。  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  

  
##  <a name="queryinterface"></a>CComObjectNoLock::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求的介面識別碼。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`。 如果物件不支援這個介面，`ppvObject`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="release"></a>CComObjectNoLock::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**版本**傳回值，可能有助於診斷或測試。 在非偵錯組建中，**版本**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

