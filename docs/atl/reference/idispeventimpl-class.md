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
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329761"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 類別

此類提供方法的`IDispatch`實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

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
源物件的唯一標識符。 當`IDispEventImpl`複合控制項的基類是時,使用此參數使用所需包含控制項的資源 ID。 在其他情況下,使用任意正整數。

*T*<br/>
使用者的類,派生自`IDispEventImpl`。

*皮迪德*<br/>
指向此類實現的事件不介面的IID的指標。 此介面必須在類型庫中定義,該類型庫由*plibid、wMajor*和*wMinor*表示。 *wMajor*

*普利比德*<br/>
指向類型庫的指標,用於定義*pdiid*指向的調度介面。 如果 **&GUID_NULL,** 類型庫將從源事件的物件載入。

*w 主要*<br/>
類型程式庫的主要版本。 預設值為 0。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*提赫班*<br/>
用於管理*T*的類型資訊的類。預設值是類型的`CComTypeInfoHolder`類。但是,您可以通過提供以外`CComTypeInfoHolder`的類型的類來覆蓋此範本參數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用於管理類型資訊的類。 預設值為 `CComTypeInfoHolder`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[IDispEventImpl::IDispeventImpl](#idispeventimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispeventimpl::從Id獲取Funcinfo](#getfuncinfofromid)|尋找指定調度標識符的函數索引。|
|[IDispeventimpl::獲取名稱的 Idds](#getidsofnames)|將單個成員和一組可選的參數名稱映射到相應的整數 DISPID。|
|[IDispEventImpl::取得類型資訊](#gettypeinfo)|檢索對象的類型資訊。|
|[IDispEventImpl::取得類型資訊計數](#gettypeinfocount)|檢索類型資訊介面的數量。|
|[IDispeventImpl::取得使用者定義類型](#getuserdefinedtype)|檢索使用者定義類型的基本類型。|

## <a name="remarks"></a>備註

`IDispEventImpl`提供了一種實現事件介面的方法,而無需為該介面上的每個方法/事件提供實現代碼。 `IDispEventImpl`提供了方法的`IDispatch`實現。 您只需為您感興趣的事件提供實現。

`IDispEventImpl`與類中的事件接收器映射結合使用,將事件路由到相應的處理程式函數。 要使用此類:

向要處理的每個物件上每個事件的事件向事件接收器映射添加[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)宏。 當用作`IDispEventImpl`複合控制件的基類時,可以調用[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)建立和斷開事件接收器映射中所有條目的事件源的連接。 在其他情況下,或為了進行更大的控制,請致電[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)以建立源物件和基類之間的連接。 致電[DispEventUn 建議](idispeventsimpleimpl-class.md#dispeventunadvise)斷開連接。

您必須從`IDispEventImpl`(使用*nID*的唯一值 )派生出需要為其處理事件的每個物件。 可以通過對一個源物件取消建議來重用基類,然後針對不同的源物件提供建議,但一次由單個物件可以處理的最大源物件數受基類`IDispEventImpl`數的限制。

`IDispEventImpl`提供與[IDispEventSimple](../../atl/reference/idispeventsimpleimpl-class.md)相同的功能,只不過它從類型庫中獲取有關介面的類型資訊,而不是將其作為指向[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構的指標提供。 當您`IDispEventSimpleImpl`沒有描述事件介面的類型庫或希望避免與使用類型庫關聯的開銷時,請使用。

> [!NOTE]
> `IDispEventImpl`並提供`IDispEventSimpleImpl`它們自己的實現`IUnknown::QueryInterface`,`IDispEventImpl`使每個`IDispEventSimpleImpl`類和基項充當單獨的 COM 識別,同時仍然允許直接存取主 COM 物件中的類成員。

ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

有關詳細資訊,請參閱支援[IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_IDispEvent`

`_IDispEventLocator`

[IDispevent 簡單](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispeventimpl::從Id獲取Funcinfo

尋找指定調度標識符的函數索引。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]對函數 ID 的引用。

*不一名會員*<br/>
[在]函數的調度 ID。

*lcid*<br/>
[在]函數 ID 的區域設置上下文。

*info*<br/>
[在]指示如何調用函數的結構。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispeventimpl::獲取名稱的 Idds

將單個成員與一組選擇參數名稱映射到一個非整數 DISPID,可用於後續呼叫[IDispatch:::invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

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

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::取得類型資訊

擷取物件的類型資訊，可以用來取得介面的類型資訊。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::取得類型資訊計數

擷取物件提供的類型資訊介面數目 (0 或 1)。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>備註

請參考 IDispatch:在 Windows SDK 中[取得類型資訊 。](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispeventImpl::取得使用者定義類型

檢索使用者定義類型的基本類型。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>參數

*Pti*<br/>
[在]指向包含使用者定義類型的[ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo)介面的指標。

*Hrt*<br/>
[在]要檢索的類型說明的句柄。

### <a name="return-value"></a>傳回值

變體的類型。

### <a name="remarks"></a>備註

請參考[ITypeInfo::取得參考類型資訊](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)。

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispeventImpl

建構函式。 儲存樣本參數*plibid、pdiid、wMajor*和*wMajor* *wMinor 的值*。 *plibid*

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass

此 typedef 是類範本參數*tihclass*的實體。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>備註

預設情況下,類別為`CComTypeInfoHolder`。 `CComTypeInfoHolder`管理類的類型資訊。

## <a name="see-also"></a>另請參閱

[_ATL_FUNC_INFO結構](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispevent 簡單簡單課程](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[類別概觀](../../atl/atl-class-overview.md)
