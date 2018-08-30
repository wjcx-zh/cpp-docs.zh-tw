---
title: CComObjectNoLock 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85332341e1a229ce5110153c0ad6195ef0ad42c4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208171"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 類別
這個類別會實作`IUnknown`的非彙總的物件，但是不會遞增模組鎖定計數的建構函式。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>參數  
 *基底*  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，因為您想要在物件上支援從任何其他介面。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|建構函式。|  
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|遞增參考計數物件上。|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|傳回所要求介面的指標。|  
|[CComObjectNoLock::Release](#release)|遞減參考計數物件。|  
  
## <a name="remarks"></a>備註  
 `CComObjectNoLock` 類似於[CComObject](../../atl/reference/ccomobject-class.md) ，因為它會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)非彙總的物件; 不過，`CComObjectNoLock`中建構函式會遞增模組的鎖定計數。  
  
 使用 ATL`CComObjectNoLock`內部的 class factory。 一般情況下，您不會直接使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>  CComObjectNoLock::AddRef  
 遞增參考計數物件上。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，這個值可能有助於診斷或測試。  
  
##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock  
 建構函式。 不同於[CComObject](../../atl/reference/ccomobject-class.md)，不會遞增模組鎖定計數。  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>參數  
 <em>void\*</em>  
 [in]不使用這個未命名的參數。 存在與其他對稱`CComXXXObjectXXX`建構函式。  
  
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
 *iid*  
 [in]所要求的介面識別碼。  
  
 *ppvObject*  
 [out]所識別之介面指標的指標*iid*。 如果物件不支援這個介面， *ppvObject*設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="release"></a>  CComObjectNoLock::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建`Release`傳回值，這個值可能有助於診斷或測試。 在非偵錯組建中，`Release`一律會傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
