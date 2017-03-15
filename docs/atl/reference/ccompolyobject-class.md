---
title: "CComPolyObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATL.CComPolyObject<contained>
- ATL::CComPolyObject
- ATL::CComPolyObject<contained>
- ATL.CComPolyObject
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 37be4c985983cb760246a4a2450c27d175d1f440
ms.lasthandoff: 02/24/2017

---
# <a name="ccompolyobject-class"></a>CComPolyObject 類別
這個類別會實作**IUnknown**彙總或非彙總的物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>參數  
 `contained`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|建構函式。|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|物件的參考計數會遞增。|  
|[CComPolyObject::CreateInstance](#createinstance)|（靜態）可讓您建立新**CComPolyObject** `contained` ** > **物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|執行的最後一個初始化`m_contained`。|  
|[CComPolyObject::FinalRelease](#finalrelease)|執行最終解構`m_contained`。|  
|[CComPolyObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|  
|[CComPolyObject::Release](#release)|物件的參考計數遞減。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|委派**IUnknown**呼叫的外部未知，如果物件彙總或**IUnknown**如果物件不會彙總的物件。|  
  
## <a name="remarks"></a>備註  
 `CComPolyObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總或非彙總的物件。  
  
 執行個體時`CComPolyObject`會建立外部的值未知已核取。 如果是**NULL**， **IUnknown**實作非彙總的物件。 如果不是外部的未知**NULL**， **IUnknown**彙總物件實作。  
  
 使用的優點`CComPolyObject`是，您不需要同時[CComAggObject](../../atl/reference/ccomaggobject-class.md)和[CComObject](../../atl/reference/ccomobject-class.md)模組處理彙總及非彙總的情況。 單一`CComPolyObject`物件會處理這兩種情況。 這表示模組中存在的 vtable 只有一個複本，以及一份函式。 如果您的 vtable 很大，這可大幅減少模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`可能會導致較大的模組大小，因為沒有最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。  
  
 如果`DECLARE_POLY_AGGREGATABLE`巨集在您的物件類別定義中，指定`CComPolyObject`會用來建立您的物件。 `DECLARE_POLY_AGGREGATABLE`將會自動宣告如果您使用 ATL 專案精靈 來建立完整控制權 」 或 Internet Explorer 控制項。  
  
 如果彙總，`CComPolyObject`物件都有它自己**IUnknown**從外部物件的個別**IUnknown**，並維護其本身的參考計數。 `CComPolyObject`使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)委派給外部未知。  
  
 如需彙總的詳細資訊，請參閱文章[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-nameaddrefa--ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef  
 在物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="a-nameccompolyobjecta--ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 建構函式。  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]如果物件是要彙總的外部未知的指標或**NULL**如果物件不會彙總的物件。  
  
### <a name="remarks"></a>備註  
 初始化`CComContainedObject`資料成員[m_contained](#m_contained)，和模組鎖定計數遞增。  
  
 解構函式會遞減模組鎖定計數。  
  
##  <a name="a-namedtora--ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 解構函式。  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源，呼叫[FinalRelease](#finalrelease)，和模組的鎖定計數遞減。  
  
##  <a name="a-namecreateinstancea--ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CreateInstance  
 可讓您建立新**CComPolyObject** `contained` ** > **物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 [out]指標**CComPolyObject** `contained` ** > **指標。 如果`CreateInstance`不成功，`pp`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 傳回的物件有參考計數為零，因此呼叫`AddRef`立即，然後使用**版本**當您完成時釋放物件指標的參考。  
  
 如果您不需要直接存取物件，但仍想要建立新的物件，而不需要的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改。  
  
##  <a name="a-namefinalconstructa--ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 呼叫物件建構的最後階段，這個方法會執行任何最後的初始設定上[m_contained](#m_contained)資料成員。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namefinalreleasea--ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease  
 在物件解構期間呼叫，這個方法會釋放[m_contained](#m_contained)資料成員。  
  
```
void FinalRelease();
```  
  
##  <a name="a-namemcontaineda--ccompolyobjectmcontained"></a><a name="m_contained"></a>CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自您的類別。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>參數  
 `contained`  
 [in]您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
### <a name="remarks"></a>備註  
 **IUnknown**透過呼叫`m_contained`如果物件彙總，或會委派給外部未知**IUnknown**如果物件不會彙總此物件。  
  
##  <a name="a-namequeryinterfacea--ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject::QueryInterface  
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
 [in]所要求的介面識別碼。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`。 如果物件不支援這個介面，`ppvObject`設為**NULL**。  
  
 `pp`  
 [out]所識別的介面指標**__uuidof(Q)**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果所要求的介面的彙總物件**IUnknown**，`QueryInterface`傳回彙總物件本身的指標**IUnknown**並遞增參考計數。 否則，這個方法會查詢介面，透過`CComContainedObject`資料成員[m_contained](#m_contained)。  
  
##  <a name="a-namereleasea--ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**版本**傳回值，可能有助於診斷或測試。 在非偵錯組建中，**版本**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](http://msdn.microsoft.com/library/7569e738-cfbc-4404-ba1d-78dcefa3bdb3)   
 [類別概觀](../../atl/atl-class-overview.md)

