---
title: CComAggObject 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426a01c1957b276174b8b36884605b69dd501de8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364215"
---
# <a name="ccomaggobject-class"></a>CComAggObject 類別
這個類別會實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總物件的介面。 根據定義，彙總的物件會包含在外部物件。 `CComAggObject`類別是類似於[Ccomobject< 類別](../../atl/reference/ccomobject-class.md)，只不過它會公開給外部用戶端直接存取的介面。  
  
## <a name="syntax"></a>語法  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>參數  
 `contained`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|建構函式。|  
|[CComAggObject:: ~ CComAggObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|在彙總物件的參考計數遞增。|  
|[CComAggObject::CreateInstance](#createinstance)|此靜態函式可讓您建立新**CComAggObject <** `contained` **>** 物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComAggObject::FinalConstruct](#finalconstruct)|會執行最後的初始化`m_contained`。|  
|[CComAggObject::FinalRelease](#finalrelease)|執行最終解構`m_contained`。|  
|[CComAggObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|  
|[CComAggObject::Release](#release)|彙總物件的參考計數遞減。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|委派`IUnknown`呼叫的外部未知。|  
  
## <a name="remarks"></a>備註  
 `CComAggObject` 實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總的物件。 `CComAggObject` 有它自己**IUnknown**介面，個別從外部物件**IUnknown**介面，並會維護其本身的參考計數。  
  
 如需彙總的詳細資訊，請參閱文章[ATL COM 物件基礎觀念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>  CComAggObject::AddRef  
 在彙總物件的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject  
 建構函式。  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]外部未知。  
  
### <a name="remarks"></a>備註  
 初始化`CComContainedObject`成員[m_contained](#m_contained)，和模組鎖定計數遞增。  
  
 解構函式遞減模組鎖定計數。  
  
##  <a name="dtor"></a>  CComAggObject:: ~ CComAggObject  
 解構函式。  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源，呼叫[FinalRelease](#finalrelease)，並遞減模組鎖定計數。  
  
##  <a name="createinstance"></a>  CComAggObject::CreateInstance  
 此靜態函式可讓您建立新**CComAggObject <** `contained` **>** 物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 [out]指標 **CComAggObject\<* * * 包含* **>** 指標。 如果`CreateInstance`不成功，`pp`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 傳回的物件有參考計數為零，因此呼叫`AddRef`立即，然後使用**發行**當您完成時釋放物件指標的參考。  
  
 如果您執行不需要直接存取物件，但仍想要建立新的物件沒有的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改為。  
  
##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct  
 在物件建構的最後階段期間呼叫，這個方法會執行任何最後的初始化上[m_contained](#m_contained)成員。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>  CComAggObject::FinalRelease  
 在對物件解構期間呼叫，這個方法會釋放[m_contained](#m_contained)成員。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComAggObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自您的類別。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>參數  
 `contained`  
 [in]您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
### <a name="remarks"></a>備註  
 所有**IUnknown**透過呼叫`m_contained`會委派給外部未知。  
  
##  <a name="queryinterface"></a>  CComAggObject::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求介面的識別項。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`。 如果物件不支援這個介面，`ppvObject`設**NULL**。  
  
 `pp`  
 [out]型別所識別的介面指標的指標`Q`。 如果物件不支援這個介面，`pp`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果要求的介面是**IUnknown**，`QueryInterface`讓指標回到彙總物件本身**IUnknown**並遞增參考計數。 否則，此方法會查詢介面透過`CComContainedObject`成員[m_contained](#m_contained)。  
  
##  <a name="release"></a>  CComAggObject::Release  
 彙總物件的參考計數遞減。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**發行**傳回值，可能有助於診斷或測試。 在非偵錯組建**發行**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [Ccomobject< 類別](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [類別概觀](../../atl/atl-class-overview.md)
