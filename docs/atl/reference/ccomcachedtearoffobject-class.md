---
title: CComCachedTearOffObject 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62ed04d8e54e4bf107ae12b9a4165b663c9d10d8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203867"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 類別
這個類別會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)撕下介面。  
  
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
 您分割的類別，衍生自`CComTearOffObjectBase`和要分割物件以支援的介面。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|建構函式。|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|參考計數會遞增`CComCachedTearOffObject`物件。|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|呼叫`m_contained::FinalConstruct`（分割類別的方法）。|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|呼叫`m_contained::FinalRelease`（分割類別的方法）。|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|將指標傳回至`IUnknown`的`CComCachedTearOffObject`物件，或要求的介面，在分割類別 (類別`contained`)。|  
|[CComCachedTearOffObject::Release](#release)|遞減參考計數的`CComCachedTearOffObject`物件，並終結它，如果參考計數為 0。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A`CComContainedObject`物件衍生自您分割的類別 (類別`contained`)。|  
  
## <a name="remarks"></a>備註  
 `CComCachedTearOffObject` 會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)撕下介面。 此類別與不同`CComTearOffObject`在於`CComCachedTearOffObject`都有它自己`IUnknown`個別擁有者物件的`IUnknown`（擁有者是為其分割所建立的物件）。 `CComCachedTearOffObject` 都會維護它自己在參考計數其`IUnknown`和參考計數為零時之後, 可對本身進行刪除。 不過，如果您針對任何其分割的查詢介面，擁有者物件的參考計數`IUnknown`會遞增。  
  
 如果`CComCachedTearOffObject`物件實作分割已經具現化，和針對同樣地，相同查詢的分割介面`CComCachedTearOffObject`會重複使用物件。 相反地，如果分割介面來實作`CComTearOffObject`擁有者物件，透過再次查詢的另一個`CComTearOffObject`會具現化。  
  
 擁有者類別必須實作`FinalRelease`並呼叫`Release`上的快取`IUnknown`如`CComCachedTearOffObject`，這將會遞減參考計數。 這會導致`CComCachedTearOffObject`的`FinalRelease`呼叫，並刪除分割。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>  CComCachedTearOffObject::AddRef  
 參考計數遞增`CComCachedTearOffObject`1 的物件。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，這個值可能有助於診斷和測試。  
  
##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject  
 建構函式。  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 *pv*  
 [in]指標`IUnknown`的`CComCachedTearOffObject`。  
  
### <a name="remarks"></a>備註  
 初始化`CComContainedObject`成員[m_contained](#m_contained)。  
  
##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 解構函式。  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源並呼叫[FinalRelease](#finalrelease)。  
  
##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct  
 呼叫`m_contained::FinalConstruct`來建立`m_contained`，則`CComContainedObject` <  `contained`> 用來存取您的分割類別所實作的介面的物件。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease  
 呼叫`m_contained::FinalRelease`釋放`m_contained`，則`CComContainedObject` <  `contained`> 物件。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自您分割的類別。  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>參數  
 *包含*  
 [in]您分割的類別，衍生自`CComTearOffObjectBase`和要分割物件以支援的介面。  
  
### <a name="remarks"></a>備註  
 方法`m_contained`繼承用來透過快取分割物件的存取分割中的介面分割類別`QueryInterface`， `FinalConstruct`，和`FinalRelease`。  
  
##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 *iid*  
 [in]所要求介面的 GUID。  
  
 *ppvObject*  
 [out]所識別之介面指標的指標*iid*，或如果找不到介面則為 NULL。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 要求的介面是否`IUnknown`，將指標傳回至`CComCachedTearOffObject`的自己`IUnknown`並遞增參考計數。 否則，查詢上撕下類別使用的介面[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法繼承自`CComObjectRootEx`。  

  
##  <a name="release"></a>  CComCachedTearOffObject::Release  
 遞減參考計數加 1，如果參考計數為 0，會刪除`CComCachedTearOffObject`物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在非偵錯組建中，一律會傳回 0。 在偵錯組建中，傳回值，可能有助於診斷或測試。  
  
## <a name="see-also"></a>另請參閱  
 [CComTearOffObject 類別](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
