---
title: "CComContainedObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3579d4080b4dba130b58592fa47efd636805ed1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 類別
這個類別會實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)委派給擁有者物件，以**IUnknown**。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|建構函式。 初始化擁有者物件的成員指標`IUnknown`。|  
|[CComContainedObject:: ~ CComContainedObject](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|擁有者物件上的參考計數遞增。|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|擷取擁有者物件`IUnknown`。|  
|[CComContainedObject::QueryInterface](#queryinterface)|擷取擁有者物件上所要求介面的指標。|  
|[CComContainedObject::Release](#release)|擁有者物件的參考計數遞減。|  
  
## <a name="remarks"></a>備註  
 使用 ATL`CComContainedObject`類別中[CComAggObject](../../atl/reference/ccomaggobject-class.md)， [CComPolyObject](../../atl/reference/ccompolyobject-class.md)，和[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)。 `CComContainedObject`實作[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)委派給擁有者物件，以**IUnknown**。 （擁有者是在外部物件的彙總或為其建立的分割介面的物件）。`CComContainedObject`呼叫`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`、 透過所有繼承`Base`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>CComContainedObject::AddRef  
 擁有者物件上的參考計數遞增。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject  
 建構函式。  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 [in]擁有者物件**IUnknown**。  
  
### <a name="remarks"></a>備註  
 設定`m_pOuterUnknown`成員指標 (透過繼承`Base`類別) 至`pv`。  
  
##  <a name="dtor"></a>CComContainedObject:: ~ CComContainedObject  
 解構函式。  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown  
 傳回`m_pOuterUnknown`成員指標 (透過繼承*基底*類別)，其中保存擁有者物件**IUnknown**。  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>傳回值  
 擁有者物件**IUnknown**。  
  
### <a name="remarks"></a>備註  
 這個方法可能是虛擬如果`Base`已宣告[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)巨集。  
  
##  <a name="queryinterface"></a>CComContainedObject::QueryInterface  
 擷取擁有者物件上所要求介面的指標。  
  
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
  
##  <a name="release"></a>CComContainedObject::Release  
 擁有者物件的參考計數遞減。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**發行**傳回值，可能有助於診斷或測試。 在非偵錯組建**發行**一律傳回 0。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
