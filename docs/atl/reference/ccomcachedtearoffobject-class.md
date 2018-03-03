---
title: "CComCachedTearOffObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89240e913f46a3522062317da8089c3ae4bd81ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 類別
這個類別會實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)撕介面。  
  
## <a name="syntax"></a>語法  
  
```
template
 <class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
 ::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>參數  
 `contained`  
 撕下類別，衍生自`CComTearOffObjectBase`和要分割物件以支援的介面。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|建構函式。|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|參考計數遞增`CComCachedTearOffObject`物件。|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|呼叫`m_contained::FinalConstruct`（撕類別的方法）。|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|呼叫`m_contained::FinalRelease`（撕類別的方法）。|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|將指標傳回至`IUnknown`的`CComCachedTearOffObject`物件，或在分割類別所要求介面 (類別`contained`)。|  
|[CComCachedTearOffObject::Release](#release)|遞減參考計數的`CComCachedTearOffObject`物件，並終結它，如果參考計數為 0。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A`CComContainedObject`物件衍生自撕下類別 (類別`contained`)。|  
  
## <a name="remarks"></a>備註  
 `CComCachedTearOffObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)撕介面。 這個類別不同於`CComTearOffObject`在於`CComCachedTearOffObject`都有它自己**IUnknown**個別擁有者物件從**IUnknown** （擁有者為其分割為所建立的物件）。 `CComCachedTearOffObject`會維護其本身參考計數在其**IUnknown**並刪除本身一旦其參考計數為零。 不過，如果您查詢其分割的任何介面、 擁有者物件的參考計數**IUnknown**會遞增。  
  
 如果`CComCachedTearOffObject`物件撕實作已經具現化，而且同樣地，具有相同查詢的分割介面`CComCachedTearOffObject`會重複使用物件。 相反地，如果實作分割介面`CComTearOffObject`擁有者物件，透過再次查詢的另一個`CComTearOffObject`會具現化。  
  
 擁有者類別必須實作`FinalRelease`和呼叫**發行**上的快取**IUnknown**如`CComCachedTearOffObject`，這會遞減參考計數。 這會導致`CComCachedTearOffObject`的`FinalRelease`呼叫及刪除分割。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>CComCachedTearOffObject::AddRef  
 參考計數遞增`CComCachedTearOffObject`1 物件。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject  
 建構函式。  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]指標**IUnknown**的`CComCachedTearOffObject`。  
  
### <a name="remarks"></a>備註  
 初始化`CComContainedObject`成員[m_contained](#m_contained)。  
  
##  <a name="dtor"></a>CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 解構函式。  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源並呼叫[FinalRelease](#finalrelease)。  
  
##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct  
 呼叫**m_contained::FinalConstruct**建立`m_contained`、 `CComContainedObject` <  `contained`> 用來存取您的分割類別所實作的介面的物件。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease  
 呼叫**m_contained::FinalRelease**釋放`m_contained`、 `CComContainedObject` <  `contained`> 物件。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自撕下類別。  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>參數  
 `contained`  
 [in]撕下類別，衍生自`CComTearOffObjectBase`和要分割物件以支援的介面。  
  
### <a name="remarks"></a>備註  
 方法`m_contained`繼承用來分割類別中透過存取快取分割物件的`QueryInterface`， `FinalConstruct`，和`FinalRelease`。  
  
##  <a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`，或**NULL**如果找不到介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果要求的介面是**IUnknown**，將指標傳回至`CComCachedTearOffObject`的自己**IUnknown**並遞增參考計數。 否則，查詢上您分割類別使用的介面[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法繼承自`CComObjectRootEx`。  

  
##  <a name="release"></a>CComCachedTearOffObject::Release  
 遞減參考計數 1，如果參考計數為 0，會刪除`CComCachedTearOffObject`物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在非偵錯組建中，一律傳回 0。 在偵錯組建中，傳回值，可能有助於診斷或測試。  
  
## <a name="see-also"></a>請參閱  
 [CComTearOffObject 類別](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
