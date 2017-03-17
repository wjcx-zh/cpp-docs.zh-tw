---
title: "CComAggObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 29
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
ms.openlocfilehash: 386ab09418c879c0de0d82d729a3de1b2e270016
ms.lasthandoff: 02/24/2017

---
# <a name="ccomaggobject-class"></a>CComAggObject 類別
這個類別會實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總物件的介面。 根據定義，彙總的物件會包含在外部的物件。 `CComAggObject`類別是類似於[CComObject 類別](../../atl/reference/ccomobject-class.md)，只不過它會公開給外部用戶端直接存取的介面。  
  
## <a name="syntax"></a>語法  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>參數  
 `contained`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|建構函式。|  
|[CComAggObject:: ~ CComAggObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|在彙總物件的參考計數遞增。|  
|[CComAggObject::CreateInstance](#createinstance)|這個靜態函式可讓您建立新**CComAggObject** `contained` ** > **物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComAggObject::FinalConstruct](#finalconstruct)|執行的最後一個初始化`m_contained`。|  
|[CComAggObject::FinalRelease](#finalrelease)|執行最終解構`m_contained`。|  
|[CComAggObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|  
|[CComAggObject::Release](#release)|遞減參考計數在彙總的物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|委派`IUnknown`呼叫的外部未知。|  
  
## <a name="remarks"></a>備註  
 `CComAggObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總的物件。 `CComAggObject`都有它自己**IUnknown**介面，從外部物件的個別**IUnknown**介面，並維護其本身的參考計數。  
  
 如需彙總的詳細資訊，請參閱文章[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="addref"></a>CComAggObject::AddRef  
 在彙總物件的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="ccomaggobject"></a>CComAggObject::CComAggObject  
 建構函式。  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]外部的未知。  
  
### <a name="remarks"></a>備註  
 初始化`CComContainedObject`成員[m_contained](#m_contained)，和模組鎖定計數遞增。  
  
 解構函式會遞減模組鎖定計數。  
  
##  <a name="dtor"></a>CComAggObject:: ~ CComAggObject  
 解構函式。  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源，呼叫[FinalRelease](#finalrelease)，和模組的鎖定計數遞減。  
  
##  <a name="createinstance"></a>CComAggObject::CreateInstance  
 這個靜態函式可讓您建立新**CComAggObject** `contained` ** > **物件沒有的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 [out]指標**CComAggObject\<***包含* ** > **指標。 如果`CreateInstance`不成功，`pp`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 傳回的物件有參考計數為零，因此呼叫`AddRef`立即，然後使用**版本**當您完成時釋放物件指標的參考。  
  
 如果您執行不需要直接存取物件，但仍想要建立新的物件，而不需要的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改。  
  
##  <a name="finalconstruct"></a>CComAggObject::FinalConstruct  
 呼叫物件建構的最後階段，這個方法會執行任何最後的初始設定上[m_contained](#m_contained)成員。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>CComAggObject::FinalRelease  
 在物件解構期間呼叫，這個方法會釋放[m_contained](#m_contained)成員。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComAggObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自您的類別。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>參數  
 `contained`  
 [in]您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
### <a name="remarks"></a>備註  
 所有**IUnknown**透過呼叫`m_contained`會委派給外部未知。  
  
##  <a name="queryinterface"></a>CComAggObject::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求的介面識別碼。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`。 如果物件不支援這個介面，`ppvObject`設為**NULL**。  
  
 `pp`  
 [out]型別所識別的介面指標的指標`Q`。 如果物件不支援這個介面，`pp`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果要求的介面是**IUnknown**，`QueryInterface`傳回彙總物件本身的指標**IUnknown**並遞增參考計數。 否則，這個方法會查詢介面，透過`CComContainedObject`成員[m_contained](#m_contained)。  
  
##  <a name="release"></a>CComAggObject::Release  
 遞減參考計數在彙總的物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**版本**傳回值，可能有助於診斷或測試。 在非偵錯組建中，**版本**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [CComObject 類別](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](http://msdn.microsoft.com/library/e7e568d7-04e0-4226-b5dc-224deed229ab)   
 [DECLARE_ONLY_AGGREGATABLE](http://msdn.microsoft.com/library/a54220df-4330-4e4d-b7fb-8b63dd62d337)   
 [DECLARE_NOT_AGGREGATABLE](http://msdn.microsoft.com/library/2a116c7c-bab8-4f2a-a9ad-03d7aba0f762)   
 [類別概觀](../../atl/atl-class-overview.md)

