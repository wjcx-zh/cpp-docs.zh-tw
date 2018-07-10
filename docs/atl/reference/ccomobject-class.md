---
title: Ccomobject< 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af84d64d326ed7746b76db39ef26181ab96ca88d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361475"
---
# <a name="ccomobject-class"></a>Ccomobject< 類別
這個類別會實作**IUnknown**非彙總的物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|建構函式。|  
|[CComObject::~CComObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|在物件上的參考計數遞增。|  
|[CComObject::CreateInstance](#createinstance)|（靜態）建立新`CComObject`物件。|  
|[CComObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|  
|[CComObject::Release](#release)|遞減參考計數物件。|  
  
## <a name="remarks"></a>備註  
 `CComObject` 實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)非彙總的物件。 不過，呼叫`QueryInterface`， `AddRef`，和**發行**委派給`CComObjectRootEx`。  
  
 如需有關使用`CComObject`，請參閱文章[ATL COM 物件基礎觀念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>  CComObject::AddRef  
 在物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 此函式會傳回新的遞增的參考計數物件上。 這個值可能是適用於診斷或測試。  
  
##  <a name="ccomobject"></a>  CComObject::CComObject  
 建構函式會遞增模組鎖定計數。  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>參數  
 **void\***  
 [in]不使用這個未命名的參數。 其存在與其他對稱 **CCom***XXX*`Object`*XXX* 建構函式。  
  
### <a name="remarks"></a>備註  
 解構函式遞減它。  
  
 如果`CComObject`-衍生的物件已成功建構使用**新**運算子，初始的參考計數為 0。 若要設定為適當的值 (1) 的參考計數，呼叫以[AddRef](#addref)函式。  
  
##  <a name="dtor"></a>  CComObject::~CComObject  
 解構函式。  
  
```
CComObject();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源，呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)，並遞減模組鎖定計數。  

  
##  <a name="createinstance"></a>  CComObject::CreateInstance  
 此靜態函式可讓您建立新**Ccomobject< <** `Base` **>** 物件，無需額外[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 [out]指標**Ccomobject< <** `Base` **>** 指標。 如果`CreateInstance`不成功，`pp`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 傳回的物件有參考計數為零，因此呼叫`AddRef`立即，然後使用**發行**當您完成時釋放物件指標的參考。  
  
 如果您執行不需要直接存取物件，但仍想要建立新的物件沒有的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改為。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>  CComObject::QueryInterface  
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
  
##  <a name="release"></a>  CComObject::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 此函式會傳回新的遞減參考計數物件上。 在偵錯組建中，傳回的值可能有助於診斷或測試。 在非偵錯組建**發行**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [類別概觀](../../atl/atl-class-overview.md)
