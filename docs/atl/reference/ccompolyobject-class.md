---
title: "CComPolyObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs: C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3518fd5936c4871e99eaf597f12fb3ab7cc8aff6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccompolyobject-class"></a>CComPolyObject 類別
這個類別會實作**IUnknown**彙總或非彙總物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>參數  
 `contained`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|建構函式。|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|物件的參考計數遞增。|  
|[CComPolyObject::CreateInstance](#createinstance)|（靜態）可讓您建立新**CComPolyObject <** `contained`  **>** 物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|會執行最後的初始化`m_contained`。|  
|[CComPolyObject::FinalRelease](#finalrelease)|執行最終解構`m_contained`。|  
|[CComPolyObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|  
|[CComPolyObject::Release](#release)|物件的參考計數遞減。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|委派**IUnknown**呼叫的外部未知，如果物件彙總或**IUnknown**如果物件不會彙總的物件。|  
  
## <a name="remarks"></a>備註  
 `CComPolyObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總或非彙總物件。  
  
 執行個體時`CComPolyObject`建立時，外部值不明已核取。 如果是**NULL**， **IUnknown**實作非彙總的物件。 如果不是外部未知**NULL**， **IUnknown**彙總物件，則實作。  
  
 使用的優點`CComPolyObject`是，您可以避免必須同時[CComAggObject](../../atl/reference/ccomaggobject-class.md)和[Ccomobject<](../../atl/reference/ccomobject-class.md)處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 這表示您可以在模組中存在 vtable 只能有一個複本和一份函式。 如果您的 vtable 很大，這可以大幅降低模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`會造成較大的模組大小因為沒有最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。  
  
 如果`DECLARE_POLY_AGGREGATABLE`巨集在您的物件類別定義中，指定`CComPolyObject`將用來建立您的物件。 `DECLARE_POLY_AGGREGATABLE`會自動被宣告為如果您使用 ATL 專案精靈來建立完整控制權 」 或 Internet Explorer 控制項。  
  
 如果彙總，`CComPolyObject`物件都有它自己**IUnknown**、 分開的外部物件**IUnknown**，並維護其本身的參考計數。 `CComPolyObject`使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)委派給外部未知。  
  
 如需彙總的詳細資訊，請參閱文章[ATL COM 物件基礎觀念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>CComPolyObject::AddRef  
 在物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 建構函式。  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]如果物件是要彙總的外部未知的指標或**NULL**如果物件不會彙總的物件。  
  
### <a name="remarks"></a>備註  
 初始化`CComContainedObject`資料成員[m_contained](#m_contained)，和模組鎖定計數遞增。  
  
 解構函式遞減模組鎖定計數。  
  
##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 解構函式。  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源，呼叫[FinalRelease](#finalrelease)，並遞減模組鎖定計數。  
  
##  <a name="createinstance"></a>CComPolyObject::CreateInstance  
 可讓您建立新**CComPolyObject <** `contained`  **>** 物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 [out]指標**CComPolyObject <** `contained`  **>** 指標。 如果`CreateInstance`不成功，`pp`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 傳回的物件有參考計數為零，因此呼叫`AddRef`立即，然後使用**發行**當您完成時釋放物件指標的參考。  
  
 如果您不需要直接存取物件，但仍想要建立新的物件沒有的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改為。  
  
##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 在物件建構的最後階段期間呼叫，這個方法會執行任何最後的初始化上[m_contained](#m_contained)資料成員。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>CComPolyObject::FinalRelease  
 在對物件解構期間呼叫，這個方法會釋放[m_contained](#m_contained)資料成員。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自您的類別。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>參數  
 `contained`  
 [in]您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
### <a name="remarks"></a>備註  
 **IUnknown**透過呼叫`m_contained`如果已彙總物件，或以委派給外部未知**IUnknown**如果物件不會彙總此物件。  
  
##  <a name="queryinterface"></a>CComPolyObject::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>參數  
 `Q`  
 COM 介面。  
  
 `iid`  
 [in]所要求介面的識別項。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`。 如果物件不支援這個介面，`ppvObject`設**NULL**。  
  
 `pp`  
 [out]所識別的介面指標**__uuidof(Q)**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 彙總物件，如果要求的介面是**IUnknown**，`QueryInterface`讓指標回到彙總物件本身**IUnknown**並遞增參考計數。 否則，此方法會查詢介面透過`CComContainedObject`資料成員[m_contained](#m_contained)。  
  
##  <a name="release"></a>CComPolyObject::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**發行**傳回值，可能有助於診斷或測試。 在非偵錯組建**發行**一律傳回 0。  
  
## <a name="see-also"></a>請參閱  
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [類別概觀](../../atl/atl-class-overview.md)
