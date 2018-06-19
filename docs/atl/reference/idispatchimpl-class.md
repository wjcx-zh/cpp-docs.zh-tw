---
title: IDispatchImpl 類別 |Microsoft 文件
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
ms.openlocfilehash: 7fddf556eba07264f6ea0b01edea3e3d1e8a3a7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364362"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 類別
提供的預設實作`IDispatch`雙重介面的一部分。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
 [輸入] `T`  
 雙重介面。  
  
 [輸入] `piid`  
 指向 IID 的`T`。  
  
 [輸入] `plibid`  
 包含介面的相關資訊的類型程式庫的 LIBID 指標。 根據預設，會傳遞伺服器層級類型程式庫。  
  
 [輸入] `wMajor`  
 類型程式庫的主要版本。 根據預設，值為 1。  
  
 [輸入] `wMinor`  
 類型程式庫的次要版本。 根據預設，值為 0。  
  
 [輸入] `tihclass`  
 用來管理的類型資訊的類別`T`。 預設值為 `CComTypeInfoHolder`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|建構函式。 呼叫`AddRef`雙重介面的型別資訊會管理受保護的成員變數上。 此解構函式會呼叫 `Release`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|將一組名稱對應至一組對應的分派識別項 (Dispatch Identifier)。|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|擷取雙重介面的型別資訊。|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|判斷是否有型別資訊供雙重介面。|  
|[IDispatchImpl::Invoke](#invoke)|提供存取權的方法和雙重介面所公開的屬性。|  
  
## <a name="remarks"></a>備註  
 `IDispatchImpl` 提供的預設實作`IDispatch`任何物件上的雙重介面的一部分。 雙重介面衍生自`IDispatch`，並使用只有 Automation 相容類型。 像分配介面，雙重介面支援早期繫結和晚期繫結。不過，雙重介面也支援 vtable 繫結。  
  
 下列範例示範典型實作`IDispatchImpl`。  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 根據預設，`IDispatchImpl`類別查閱的類型資訊`T`登錄中。 若要實作取消註冊的介面，您可以使用`IDispatchImpl`類別，而不使用預先定義的版本號碼來存取登錄。 如果您建立`IDispatchImpl`具有 0xFFFF 做為值的物件`wMajor`和 0xFFFF 做為值`wMinor`、`IDispatchImpl`類別從.dll 檔案，而不是登錄中擷取類型程式庫。  
  
 `IDispatchImpl` 包含型別的靜態成員`CComTypeInfoHolder`管理雙重介面的型別資訊。 如果您有多個物件實作相同的雙重介面，只有一個執行個體`CComTypeInfoHolder`用。  
  
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
 請參閱[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) Windows SDK 中。  
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 擷取雙重介面的型別資訊。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) Windows SDK 中。  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 判斷是否有型別資訊供雙重介面。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱`IDispatch::GetTypeInfoCount`Windows SDK 中。  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 建構函式。 呼叫`AddRef`雙重介面的型別資訊會管理受保護的成員變數上。 解構函式呼叫**發行**。  
  
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
 請參閱[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
