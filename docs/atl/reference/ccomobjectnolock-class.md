---
title: "CComObjectNoLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a85a238d17fe279359a73d3c740406c15b92c34
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 類別
這個類別會實作**IUnknown**的非彙總的物件，但是不會遞增中建構函式的模組鎖定計數。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|建構函式。|  
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|在物件上的參考計數遞增。|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|傳回所要求介面的指標。|  
|[CComObjectNoLock::Release](#release)|遞減參考計數物件。|  
  
## <a name="remarks"></a>備註  
 `CComObjectNoLock` 類似於[Ccomobject<](../../atl/reference/ccomobject-class.md) ，它會實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)非彙總的物件; 不過，`CComObjectNoLock`建構函式中沒有增量模組鎖定計數。  
  
 使用 ATL`CComObjectNoLock`內部的 class factory。 一般情況下，您不會直接使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>  CComObjectNoLock::AddRef  
 在物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock  
 建構函式。 不同於[Ccomobject<](../../atl/reference/ccomobject-class.md)，不會遞增模組鎖定計數。  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>參數  
 **void\***  
 [in]不使用這個未命名的參數。 其存在與其他對稱 **CCom***XXX*`Object`*XXX* 建構函式。  
  
##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock  
 解構函式。  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  

  
##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求介面的識別項。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`。 如果物件不支援這個介面，`ppvObject`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="release"></a>  CComObjectNoLock::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**發行**傳回值，可能有助於診斷或測試。 在非偵錯組建**發行**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
