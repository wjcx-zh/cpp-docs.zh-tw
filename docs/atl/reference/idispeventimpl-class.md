---
title: IDispEventImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2419b4da0cad2662a246c167938d673429afbf26
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060894"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 類別

這個類別提供的實作`IDispatch`方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>參數

*nID*<br/>
來源物件的唯一識別碼。 當`IDispEventImpl`的基底類別為複合控制項，使用此參數所需的自主控制的資源識別碼。 在其他情況下，使用任意的正整數。

*T*<br/>
使用者的類別，衍生自`IDispEventImpl`。

*pdiid*<br/>
要由此類別實作的事件分配程式介面的 IID 的指標。 此介面必須定義在所表示的類型程式庫*plibid*， *wMajor*，並*wMinor*。

*plibid*<br/>
類型程式庫定義分派介面的指標所指向*pdiid*。 如果 **& GUID_NULL**，會從來源事件的物件載入類型程式庫。

*wMajor*<br/>
類型程式庫的主要版本。 預設值為 0。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*tihclass*<br/>
用來管理的類型資訊的類別*T*。預設值是類型的類別之`CComTypeInfoHolder`; 不過，您可以提供型別的類別以外的其他連線，覆寫此範本參數`CComTypeInfoHolder`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用來管理的型別資訊的類別。 根據預設， `CComTypeInfoHolder`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|找出指定的分派識別項的函式的索引。|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|將單一成員和一組選擇性的引數名稱對應至一組對應的 Dispid 的整數。|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|擷取物件的型別資訊。|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|擷取型別資訊介面數目。|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|擷取使用者定義型別的基本類型。|

## <a name="remarks"></a>備註

`IDispEventImpl` 提供實作事件分配程式介面，而不需要您的方式，提供每個方法/事件上該介面的實作程式碼。 `IDispEventImpl` 提供的實作`IDispatch`方法。 您只需要提供您感興趣處理事件的實作。

`IDispEventImpl` 適用於搭配事件接收對應，在您的類別，以將事件路由至適當的處理常式函式。 若要使用此類別：

新增[SINK_ENTRY](composite-control-macros.md#sink_entry)或是[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)針對每個您想要處理的物件上的每個事件的事件接收對應的巨集。 使用時`IDispEventImpl`複合控制項的基底類別，您可以呼叫[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)建立，並針對所有項目在事件接收對應會中斷與事件來源的連接。 在其他情況下，或大於控制項中，呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)以建立來源物件與基底類別之間的連線。 呼叫[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)中斷連線。

您必須衍生自`IDispEventImpl`(使用的唯一值*nID*) 針對每個您要處理事件的物件。 您可以藉由取消通知對一個來源物件，則建議針對不同的來源物件，重複使用的基底類別，但可由單一物件一次的來源物件的數目上限的數目受限於`IDispEventImpl`基底類別。

`IDispEventImpl` 提供與相同的功能[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，但它會從類型程式庫，而不需要它的指標當做提供取得有關介面的類型資訊[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構。 使用`IDispEventSimpleImpl`時您不具有描述事件介面的型別程式庫或不想以避免與使用類型程式庫相關聯的額外負荷。

> [!NOTE]
> `IDispEventImpl` 並`IDispEventSimpleImpl`提供其自己實作的`IUnknown::QueryInterface`啟用每個`IDispEventImpl`和`IDispEventSimpleImpl`基底類別，作為個別的 COM 識別，同時仍然允許對類別成員的直接存取，您主要的 COM 物件中。

CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

如需詳細資訊，請參閱 <<c0> [ 支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

找出指定的分派識別項的函式的索引。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]Id 函式的參考。

*dispidMember*<br/>
[in]函式的分派識別碼。

*lcid*<br/>
[in]地區設定內容的函式識別碼。

*info*<br/>
[in]結構，表示呼叫此函式的方式。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames

將單一成員和一組選擇性的引數名稱對應至一組對應的整數 Dispid，可用來在後續呼叫[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)。

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

##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo

擷取物件的類型資訊，可以用來取得介面的類型資訊。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount

擷取物件提供的類型資訊介面數目 (0 或 1)。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>備註

請參閱[IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) Windows SDK 中。

##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType

擷取使用者定義型別的基本類型。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>參數

*PTI*<br/>
[in]指標[ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo)包含使用者定義類型的介面。

*hrt*<br/>
[in]要擷取之型別描述的控制代碼。

### <a name="return-value"></a>傳回值

Variant 類型。

### <a name="remarks"></a>備註

請參閱[ITypeInfo::GetRefTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)。

##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl

建構函式。 儲存類別範本參數的值*plibid*， *pdiid*， *wMajor*，以及*wMinor*。

```
IDispEventImpl();
```

##  <a name="tihclass"></a>  IDispEventImpl::tihclass

此 typedef 是類別範本參數的執行個體*tihclass*。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>備註

根據預設，此類別是`CComTypeInfoHolder`。 `CComTypeInfoHolder` 管理類別的型別資訊。

## <a name="see-also"></a>另請參閱

[_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[類別概觀](../../atl/atl-class-overview.md)