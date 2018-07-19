---
title: IDispatchImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c30f65701aa42c3fb73a5ef544f4b4126468a29d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962575"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 類別
提供的預設實作`IDispatch`雙重介面的一部分。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
 [in]*T*  
 雙重介面。  
  
 [in]*piid*  
 指向 IID *T*。  
  
 [in]*plibid*  
 指標，包含介面的相關資訊的類型程式庫的 LIBID。 根據預設，會傳遞伺服器層級類型程式庫。  
  
 [in]*wMajor*  
 類型程式庫的主要版本。 根據預設，此值為 1。  
  
 [in]*wMinor*  
 類型程式庫的次要版本。 根據預設，此值為 0。  
  
 [in]*tihclass*  
 用來管理的類型資訊的類別*T*。預設值為 `CComTypeInfoHolder`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|建構函式。 呼叫`AddRef`管理雙重介面的型別資訊的受保護的成員變數上。 此解構函式會呼叫 `Release`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|將一組名稱對應至一組對應的分派識別項 (Dispatch Identifier)。|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|擷取的雙重介面的型別資訊。|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|判斷是否有可用的型別資訊的雙重介面。|  
|[IDispatchImpl::Invoke](#invoke)|提供存取權的方法和雙重介面所公開的屬性。|  
  
## <a name="remarks"></a>備註  
 `IDispatchImpl` 提供的預設實作`IDispatch`任何物件上的雙重介面的一部分。 雙重介面衍生自`IDispatch`，並使用只有 Automation 相容型別。 例如分配介面，雙重介面支援早期繫結和晚期繫結;不過，雙重介面也支援 vtable 繫結。  
  
 下列範例示範的典型實作`IDispatchImpl`。  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 根據預設，`IDispatchImpl`類別查閱的類型資訊*T*在登錄中。 若要實作取消註冊的介面，您可以使用`IDispatchImpl`類別，而不使用預先定義的版本號碼來存取登錄。 如果您建立`IDispatchImpl`物件具有的值 0xFFFF *wMajor*和 0xFFFF 做為值*wMinor*，`IDispatchImpl`類別的.dll 檔案，而不是從擷取類型程式庫登錄中。  
  
 `IDispatchImpl` 包含類型的靜態成員`CComTypeInfoHolder`管理雙重介面的型別資訊。 如果您有多個物件，實作相同的雙重介面，只有一個執行個體`CComTypeInfoHolder`用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames  
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
 請參閱[IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) Windows SDK 中。  
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 擷取的雙重介面的型別資訊。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) Windows SDK 中。  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 判斷是否有可用的型別資訊的雙重介面。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱`IDispatch::GetTypeInfoCount`Windows SDK 中。  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 建構函式。 呼叫`AddRef`管理雙重介面的型別資訊的受保護的成員變數上。 此解構函式會呼叫 `Release`。  
  
```
IDispatchImpl();
```  
  
##  <a name="invoke"></a>  IDispatchImpl::Invoke  
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
 請參閱[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
