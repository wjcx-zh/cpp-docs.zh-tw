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
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329800"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 類別

為雙介面部分`IDispatch`提供默認實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

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
[在]雙介面。

*皮伊德*<br/>
[在]指向*T*的 IID 的指標。

*普利比德*<br/>
[在]指向類型庫 LIBID 的指標,其中包含有關介面的資訊。 預設情況下,傳遞伺服器級類型庫。

*w 主要*<br/>
[在]類型庫的主要版本。 默認情況下,該值為 1。

*wMinor*<br/>
[在]類型庫的次要版本。 默認情況下,值為 0。

*提赫班*<br/>
[在]用於管理*T*的類型資訊的類。預設情況下,該值為`CComTypeInfoHolder`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[I 調度::I 調度](#idispatchimpl)|建構函式。 調用`AddRef`管理雙介面類型資訊的受保護成員變數。 此解構函式會呼叫 `Release`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispatchimpl:取得名稱](#getidsofnames)|將一組名稱對應至一組對應的分派識別項 (Dispatch Identifier)。|
|[IDispatchImpl::取得類型資訊](#gettypeinfo)|檢索雙介面的類型資訊。|
|[IDispatchImpl::取得類型資訊計數](#gettypeinfocount)|確定雙介面是否有可用的類型資訊。|
|[IDispatchImpl::呼叫](#invoke)|提供對雙介面公開的方法和屬性的訪問。|

## <a name="remarks"></a>備註

`IDispatchImpl`為物件上`IDispatch`任何雙介面的一部分提供默認實現。 雙介面派生自`IDispatch`並僅使用與自動化相容的類型。 與介面一樣,雙介面支援早期綁定和後期綁定;但是,雙介面還支援 vtable 綁定。

下面的示例顯示了`IDispatchImpl`的典型實現。

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

預設情況下,`IDispatchImpl`類別在註冊表中尋找*T*的類型資訊。 要實現未註冊的介面,`IDispatchImpl`可以使用類,而無需使用預定義的版本號存取註冊表。 如果創建的物件`IDispatchImpl`具有 0xFFFF 作為*wMajor*的值,0xFFFF 作為`IDispatchImpl`*wMinor*的值, 則類將從 .dll 檔而不是註冊表中檢索類型庫。

`IDispatchImpl`包含管理雙介面類型信息的`CComTypeInfoHolder`靜態類型成員。 如果有多個物件實現同一`CComTypeInfoHolder`雙介面,則僅使用

## <a name="inheritance-hierarchy"></a>繼承階層架構

`T`

`IDispatchImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchimpl:取得名稱

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

請參閱[IDispatch:獲取](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames)Windows SDK 中的名稱。

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::取得類型資訊

檢索雙介面的類型資訊。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

請參閱[IDispatch:在](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo)Windows SDK 中獲取類型資訊。

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::取得類型資訊計數

確定雙介面是否有可用的類型資訊。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>備註

請參閱`IDispatch::GetTypeInfoCount`Windows SDK。

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>I 調度::I 調度

建構函式。 調用`AddRef`管理雙介面類型資訊的受保護成員變數。 此解構函式會呼叫 `Release`。

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::呼叫

提供對雙介面公開的方法和屬性的訪問。

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

請參閱[IDispatch::](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)在 Windows SDK 中調用。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
