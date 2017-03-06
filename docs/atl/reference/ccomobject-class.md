---
title: "CComObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComObject<Base>
- ATL::CComObject
- ATL::CComObject<Base>
- ATL.CComObject
- CComObject
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
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
ms.openlocfilehash: 5f752b96d4a722fbddfcc9e5be3a82b8b12a86a1
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobject-class"></a>CComObject 類別
這個類別會實作**IUnknown**非彙總的物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|建構函式。|  
|[CComObject:: ~ CComObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|在物件上的參考計數遞增。|  
|[CComObject::CreateInstance](#createinstance)|（靜態）建立新`CComObject`物件。|  
|[CComObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|  
|[CComObject::Release](#release)|遞減參考計數物件。|  
  
## <a name="remarks"></a>備註  
 `CComObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)非彙總的物件。 不過，呼叫`QueryInterface`， `AddRef`，和**版本**委派給`CComObjectRootEx`。  
  
 如需有關使用`CComObject`，請參閱文章[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-nameaddrefa--ccomobjectaddref"></a><a name="addref"></a>CComObject::AddRef  
 在物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 此函數會傳回新的遞增的參考計數物件。 這個值可用來診斷測試。  
  
##  <a name="a-nameccomobjecta--ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject::CComObject  
 建構函式遞增模組鎖定計數。  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>參數  
 **void\***  
 [in]不使用這個未命名的參數。 它有與其他對稱**CCom***XXX*`Object`*XXX*建構函式。  
  
### <a name="remarks"></a>備註  
 解構函式遞減它。  
  
 如果`CComObject`-使用成功建構衍生的物件**新**運算子，初始的參考計數為 0。 若要設定為適當的值 (1) 的參考計數，請呼叫[AddRef](#addref)函式。  
  
##  <a name="a-namedtora--ccomobjectccomobject"></a><a name="dtor"></a>CComObject:: ~ CComObject  
 解構函式。  
  
```
CComObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源，呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)，和模組的鎖定計數遞減。  

  
##  <a name="a-namecreateinstancea--ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CreateInstance  
 這個靜態函式可讓您建立新**CComObject** `Base` ** > **物件，而不需要的額外負荷[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 [out]指標**CComObject** `Base` ** > **指標。 如果`CreateInstance`不成功，`pp`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 傳回的物件有參考計數為零，因此呼叫`AddRef`立即，然後使用**版本**當您完成時釋放物件指標的參考。  
  
 如果您執行不需要直接存取物件，但仍想要建立新的物件，而不需要的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#38;](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM&#39;](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="a-namequeryinterfacea--ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface  
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
  
##  <a name="a-namereleasea--ccomobjectrelease"></a><a name="release"></a>CComObject::Release  
 遞減參考計數物件。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 此函數會傳回新的遞減參考計數物件。 在偵錯組建中，傳回的值可能有助於診斷或測試。 在非偵錯組建中，**版本**一律傳回 0。  
  
## <a name="see-also"></a>另請參閱  
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](http://msdn.microsoft.com/library/e7e568d7-04e0-4226-b5dc-224deed229ab)   
 [DECLARE_NOT_AGGREGATABLE](http://msdn.microsoft.com/library/2a116c7c-bab8-4f2a-a9ad-03d7aba0f762)   
 [類別概觀](../../atl/atl-class-overview.md)

