---
title: "CComTearOffObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs:
- C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 3e8e997f26df1adca8050bd4d967a38297685831
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 類別
這個類別會實作撕介面。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>
class CComTearOffObject : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 撕下類別，衍生自`CComTearOffObjectBase`和要撕物件支援的介面。  
  
 ATL 實作其 tear-off 介面分成兩個階段 —`CComTearOffObjectBase`方法會處理參考計數和`QueryInterface`，雖然`CComTearOffObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|建構函式。|  
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|參考計數遞增`CComTearOffObject`物件。|  
|[CComTearOffObject::QueryInterface](#queryinterface)|傳回所要求介面的指標上撕下類別或擁有者類別。|  
|[CComTearOffObject::Release](#release)|遞減參考計數的`CComTearOffObject`物件，並將其終結。|  
  
### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|建構函式。|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 資料成員  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|指標`CComObject`衍生自擁有者類別。|  
  
## <a name="remarks"></a>備註  
 `CComTearOffObject`為個別的物件，該介面針對查詢時，才會具現化，可實作撕介面。 撕下會刪除其參考計數變成零時。 一般而言，您會建置撕介面很少使用，因為使用撕將 vtable 指標儲存在主要物件的所有執行個體的介面。  
  
 您應該衍生類別實作撕從`CComTearOffObjectBase`並從要撕物件以支援何種介面。 `CComTearOffObjectBase`被根據擁有者的類別和執行緒模型。 擁有者類別是的物件的撕正在實作的類別。 如果未指定執行緒模型，則會使用預設的執行緒模型。  
  
 您應該建立 COM 地圖撕類別。 當 ATL 具現化撕時，它會建立**CComTearOffObject\<CYourTearOffClass >**或**CComCachedTearOffObject\<CYourTearOffClass >**。  
  
 例如，在呼叫範例中，`CBeeper2`類別是撕類別和`CBeeper`類別是擁有者的類別︰  
  
 [!code-cpp[NVC_ATL_COM&#43;](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="addref"></a>CComTearOffObject::AddRef  
 參考計數遞增`CComTearOffObject`一個物件。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject  
 建構函式。  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]將轉換成指標的指標**CComObject\<擁有者 >**物件。  
  
### <a name="remarks"></a>備註  
 擁有者的參考計數遞增&1;。  
  
##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject  
 解構函式。  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源，呼叫 FinalRelease，並遞減模組鎖定計數。  
  
##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase  
 建構函式。  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>備註  
 初始化[m_pOwner](#m_powner)成員**NULL**。  
  
##  <a name="m_powner"></a>CComTearOffObject::m_pOwner  
 指標[CComObject](../../atl/reference/ccomobject-class.md)物件衍生自*擁有者*。  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>參數  
 *擁有者*  
 [in]為其撕已實作的類別。  
  
### <a name="remarks"></a>備註  
 指標初始化為**NULL**在建構期間。  
  
##  <a name="queryinterface"></a>CComTearOffObject::QueryInterface  
 擷取所要求介面的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求之介面的 IID。  
  
 `ppvObject`  
 [out]所識別的介面指標的指標`iid`，或**NULL**如果找不到介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 第一次查詢中的上撕下類別的介面。 如果介面不存在，查詢擁有者物件上的介面。 如果要求的介面是**IUnknown**，傳回**IUnknown**的擁有者。  
  
##  <a name="release"></a>CComTearOffObject::Release  
 遞減參考計數&1; 和參考計數為零，如果刪除`CComTearOffObject`。  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>傳回值  
 在非偵錯組建中，一律會傳回零。 在偵錯組建中，傳回值，可能有助於診斷或測試。  
  
## <a name="see-also"></a>另請參閱  
 [CComCachedTearOffObject 類別](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

