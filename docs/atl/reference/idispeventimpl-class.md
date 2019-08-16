---
title: IDispEventImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: e82a397b6d2abb66f773908c72a287c979e5ae1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495924"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 類別

這個類別會提供`IDispatch`方法的執行。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

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
來源物件的唯一識別碼。 當`IDispEventImpl`是複合控制項的基類時, 請針對此參數使用所需包含控制項的資源識別碼。 在其他情況下, 請使用任意正整數。

*T*<br/>
使用者的類別, 衍生自`IDispEventImpl`。

*pdiid*<br/>
這個類別所執行之事件分配介面的 IID 指標。 此介面必須定義于*plibid*、 *wMajor*和*wMinor*所表示的類型程式庫中。

*plibid*<br/>
類型程式庫的指標, 定義*pdiid*所指向的分派介面。 如果 **&AMP; GUID_Null**, 則會從來源為事件的物件載入類型程式庫。

*wMajor*<br/>
類型程式庫的主要版本。 預設值為 0。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*tihclass*<br/>
用來管理*T*之類型資訊的類別。預設值是類型`CComTypeInfoHolder`的類別, 不過, 您可以提供以外類型`CComTypeInfoHolder`的類別來覆寫此範本參數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用來管理類型資訊的類別。 預設`CComTypeInfoHolder`為。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|尋找指定分派識別碼的函數索引。|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|將單一成員和一組選擇性的引數名稱對應至一組相對應的整數 Dispid。|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|抓取物件的類型資訊。|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|抓取類型資訊介面的數目。|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|抓取使用者定義類型的基本類型。|

## <a name="remarks"></a>備註

`IDispEventImpl`提供一種方法來執行事件分配介面, 而不需要您為該介面上的每個方法/事件提供實作為程式碼。 `IDispEventImpl``IDispatch`提供方法的執行。 您只需要提供您想要處理之事件的「執行」。

`IDispEventImpl`與類別中的事件接收器對應搭配使用, 以將事件路由至適當的處理函式。 若要使用此類別:

針對您要處理的每個物件上的每個事件, 將[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)宏新增至事件接收對應。 使用`IDispEventImpl`做為複合控制項的基類時, 您可以呼叫[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)來建立和中斷與事件接收對應中所有專案之事件來源的連接。 在其他情況下, 或若要進行更好的控制, 請呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)來建立來源物件與基類之間的連接。 呼叫[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)以中斷連接。

您必須針對需要`IDispEventImpl`處理事件的每個物件, 衍生自 (針對*nID*使用唯一的值)。 您可以針對某個來源物件 unadvising 重複使用基類, 然後針對不同的來源物件進行建議, 但是單一物件可一次處理的最大來源物件數目會受到`IDispEventImpl`基類數目的限制。

`IDispEventImpl`提供與[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)相同的功能, 不同之處在于它會從型別程式庫取得介面的類型資訊, 而不是將它當做[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構的指標提供。 當`IDispEventSimpleImpl`您沒有描述事件介面的類型程式庫, 或想要避免與使用類型程式庫相關聯的額外負荷時, 請使用。

> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供自己的`IUnknown::QueryInterface`實作為, 讓`IDispEventImpl`每`IDispEventSimpleImpl`個和基類作為個別的 com 身分識別, 同時仍允許直接存取主要 COM 物件中的類別成員。

適用于 ActiveX 事件接收的 CE ATL 實作為, 只支援事件處理常式方法中 HRESULT 或 void 類型的傳回值;不支援任何其他傳回值, 且其行為未定義。

如需詳細資訊, 請參閱[支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getfuncinfofromid"></a>IDispEventImpl:: GetFuncInfoFromId

尋找指定分派識別碼的函數索引。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>參數

*iid*<br/>
在函數識別碼的參考。

*dispidMember*<br/>
在函數的分派識別碼。

*lcid*<br/>
在函數識別碼的地區設定內容。

*info*<br/>
在結構, 表示呼叫函數的方式。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="getidsofnames"></a>IDispEventImpl:: GetIDsOfNames

將單一成員和一組選擇性的引數名稱對應至相對應的整數 Dispid 集合, 可在後續呼叫[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)時使用。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 。

##  <a name="gettypeinfo"></a>IDispEventImpl:: GetTypeInfo

擷取物件的類型資訊，可以用來取得介面的類型資訊。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

##  <a name="gettypeinfocount"></a>IDispEventImpl:: GetTypeInfoCount

擷取物件提供的類型資訊介面數目 (0 或 1)。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 。

##  <a name="getuserdefinedtype"></a>IDispEventImpl:: GetUserDefinedType

抓取使用者定義類型的基本類型。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>參數

*pTI*<br/>
在包含使用者定義型別之[ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo)介面的指標。

*hrt*<br/>
在要抓取之類型描述的控制碼。

### <a name="return-value"></a>傳回值

Variant 的類型。

### <a name="remarks"></a>備註

請參閱[ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)。

##  <a name="idispeventimpl"></a>IDispEventImpl:: IDispEventImpl

建構函式。 儲存類別範本參數*plibid*、 *pdiid*、 *wMajor*和*wMinor*的值。

```
IDispEventImpl();
```

##  <a name="tihclass"></a>IDispEventImpl:: tihclass

此 typedef 是類別樣板參數*tihclass*的實例。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>備註

根據預設, 類別是`CComTypeInfoHolder`。 `CComTypeInfoHolder`管理類別的類型資訊。

## <a name="see-also"></a>另請參閱

[_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[類別總覽](../../atl/atl-class-overview.md)
