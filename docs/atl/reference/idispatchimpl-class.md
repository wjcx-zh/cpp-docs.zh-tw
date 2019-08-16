---
title: IDispatchImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495954"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 類別

提供雙重介面`IDispatch`元件的預設實值。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

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

*T*<br/>
在雙重介面。

*piid*<br/>
在*T*之 IID 的指標。

*plibid*<br/>
在類型程式庫之 LIBID 的指標, 其中包含介面的相關資訊。 根據預設, 會傳遞伺服器層級類型程式庫。

*wMajor*<br/>
在類型程式庫的主要版本。 根據預設, 此值為1。

*wMinor*<br/>
在類型程式庫的次要版本。 根據預設, 此值為0。

*tihclass*<br/>
在用來管理*T*之類型資訊的類別。預設值為 `CComTypeInfoHolder`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|建構函式。 在`AddRef`管理雙重介面之類型資訊的受保護成員變數上呼叫。 此解構函式會呼叫 `Release`。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|將一組名稱對應至一組對應的分派識別項 (Dispatch Identifier)。|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|抓取雙重介面的類型資訊。|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|判斷雙重介面是否有可用的類型資訊。|
|[IDispatchImpl::Invoke](#invoke)|提供雙重介面所公開之方法和屬性的存取權。|

## <a name="remarks"></a>備註

`IDispatchImpl`為物件上任何雙重介面`IDispatch`的部分提供預設的執行。 雙重介面衍生自`IDispatch` , 並且只使用與 Automation 相容的類型。 就像分配介面一樣, 雙重介面支援早期繫結和晚期繫結;不過, 雙重介面也支援 vtable 系結。

下列範例顯示的一般執行`IDispatchImpl`。

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

根據預設, `IDispatchImpl`類別會在登錄中查閱*T*的類型資訊。 若要執行未註冊的介面, 您可以`IDispatchImpl`使用類別, 而不需要使用預先定義的版本號碼來存取登錄。 如果您建立`IDispatchImpl`的物件具有0xffff 做為*wMajor*的值, 且0xffff 為*wMinor*的值, 則`IDispatchImpl`類別會從 .dll 檔案 (而不是登錄) 抓取類型程式庫。

`IDispatchImpl`包含類型`CComTypeInfoHolder`的靜態成員, 它會管理雙重介面的類型資訊。 如果您有多個物件執行相同的雙重介面, 則只會使用`CComTypeInfoHolder`一個的實例。

## <a name="inheritance-hierarchy"></a>繼承階層

`T`

`IDispatchImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getidsofnames"></a>IDispatchImpl:: GetIDsOfNames

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

請參閱 Windows SDK 中的[IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 。

##  <a name="gettypeinfo"></a>IDispatchImpl:: GetTypeInfo

抓取雙重介面的類型資訊。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 。

##  <a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

判斷雙重介面是否有可用的類型資訊。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>備註

請`IDispatch::GetTypeInfoCount`參閱 Windows SDK 中的。

##  <a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

建構函式。 在`AddRef`管理雙重介面之類型資訊的受保護成員變數上呼叫。 此解構函式會呼叫 `Release`。

```
IDispatchImpl();
```

##  <a name="invoke"></a>IDispatchImpl:: Invoke

提供雙重介面所公開之方法和屬性的存取權。

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

請參閱 Windows SDK 中的[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
