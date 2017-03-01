---
title: "IDispatchImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATL.IDispatchImpl
- ATL::IDispatchImpl
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
caps.latest.revision: 27
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: fff4cbc0a3f87b584f1a4211f4aad37228ed4da7
ms.lasthandoff: 02/24/2017

---
# <a name="idispatchimpl-class"></a>IDispatchImpl 類別
提供的預設實作`IDispatch`雙重介面的一部分。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0, 
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```  
  
#### <a name="parameters"></a>參數  
 [in] `T`  
 雙重介面。  
  
 [in] `piid`  
 指標的 IID `T`。  
  
 [in] `plibid`  
 包含介面的相關資訊的型別程式庫的 LIBID 指標。 根據預設，會傳遞伺服器層級類型程式庫。  
  
 [in] `wMajor`  
 型別程式庫的主要版本。 根據預設，此值為 1。  
  
 [in] `wMinor`  
 次要類型程式庫版本。 根據預設，此值為 0。  
  
 [in] `tihclass`  
 用來管理的型別資訊的類別`T`。 預設值為 `CComTypeInfoHolder`。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|建構函式。 呼叫`AddRef`管理雙重介面的型別資訊的受保護的成員變數上。 此解構函式會呼叫 `Release`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|將一組名稱對應至一組對應的分派識別項 (Dispatch Identifier)。|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|擷取雙重介面的型別資訊。|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|判斷是否有可用的型別資訊的雙重介面。|  
|[IDispatchImpl::Invoke](#invoke)|提供存取權的方法和雙重介面所公開的屬性。|  
  
## <a name="remarks"></a>備註  
 `IDispatchImpl`提供的預設實作`IDispatch`任何物件上的雙重介面的一部分。 雙重介面是衍生自`IDispatch`，並使用只有 Automation 相容的型別。 像分配介面，雙重介面可支援早期繫結和晚期繫結。不過，雙重介面也支援 vtable 繫結。  
  
 下列範例示範的典型實作`IDispatchImpl`。  
  
 [!code-cpp[NVC_ATL_COM&#47;](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 根據預設，`IDispatchImpl`類別查閱的類型資訊`T`在登錄中。 若要實作取消註冊的介面，您可以使用`IDispatchImpl`類別，而不使用預先定義的版本號碼來存取登錄。 如果您建立`IDispatchImpl`物件做為值的 0xFFFF`wMajor`和 0xFFFF 做為值`wMinor`、`IDispatchImpl`類別會從.dll 檔案，而不是登錄中擷取類型程式庫。  
  
 `IDispatchImpl`包含型別的靜態成員`CComTypeInfoHolder`管理雙重介面的型別資訊。 如果您有多個物件實作相同的雙重介面，只有一個執行個體`CComTypeInfoHolder`用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-namegetidsofnamesa--idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames  
 將一組名稱對應至一組對應的分派識別項 (Dispatch Identifier)。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfoa--idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo  
 擷取雙重介面的型別資訊。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfocounta--idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount  
 判斷是否有可用的型別資訊的雙重介面。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>備註  
 See `IDispatch::GetTypeInfoCount` in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameidispatchimpla--idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl  
 建構函式。 呼叫`AddRef`管理雙重介面的型別資訊的受保護的成員變數上。 解構函式呼叫**版本**。  
  
```
IDispatchImpl();
```  
  
##  <a name="a-nameinvokea--idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Invoke  
 提供存取權的方法和雙重介面所公開的屬性。  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```  
  
### <a name="remarks"></a>備註  
 請參閱[Excepinfo](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

