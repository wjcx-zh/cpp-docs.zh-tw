---
title: IDataObjectImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: 379dd3304d96afcd2b0e98ec4a98f1bac64d4ad9
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470767"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl 類別

這個類別提供支援制式資料傳輸和管理連接的方法。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IDataObjectImpl` 。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IDataObjectImpl：:D 通知](#dadvise)|建立資料物件和通知接收之間的連接。 這可讓通知接收器接收物件中變更的通知。|
|[IDataObjectImpl：:D Unadvise](#dunadvise)|終止先前透過建立的連接 `DAdvise` 。|
|[IDataObjectImpl：： EnumDAdvise](#enumdadvise)|建立列舉值以逐一查看目前的諮詢連接。|
|[IDataObjectImpl：： EnumFormatEtc](#enumformatetc)|建立列舉值，以逐一查看 `FORMATETC` 資料物件所支援的結構。 ATL 執行會傳回 E_NOTIMPL。|
|[IDataObjectImpl::FireDataChange](#firedatachange)|將變更通知傳回給每個「通知」接收。|
|[IDataObjectImpl：： GetCanonicalFormatEtc](#getcanonicalformatetc)|抓取邏輯上 `FORMATETC` 對等結構，使其更複雜。 ATL 執行會傳回 E_NOTIMPL。|
|[IDataObjectImpl：：操作](#getdata)|將資料從資料物件傳送到用戶端。 資料會在結構中描述 `FORMATETC` ，並透過 `STGMEDIUM` 結構傳送。|
|[IDataObjectImpl：： GetDataHere](#getdatahere)|類似于 `GetData` ，但用戶端必須配置 `STGMEDIUM` 結構。 ATL 執行會傳回 E_NOTIMPL。|
|[IDataObjectImpl::QueryGetData](#querygetdata)|判斷資料物件是否支援 `FORMATETC` 傳送資料的特定結構。 ATL 執行會傳回 E_NOTIMPL。|
|[IDataObjectImpl：： SetData](#setdata)|將資料從用戶端傳送至資料物件。 ATL 執行會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)介面提供支援制式資料傳輸的方法。 `IDataObject`會使用標準格式結構[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1)來取出和儲存資料。

`IDataObject`也會管理連接，以通知接收處理資料變更通知。 為了讓用戶端從資料物件接收資料變更通知，用戶端必須在稱為「建議接收」的物件上，執行[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面。 當用戶端呼叫時 `IDataObject::DAdvise` ，會在資料物件和通知接收之間建立連接。

類別會 `IDataObjectImpl` 提供的預設執行 `IDataObject` ，並 `IUnknown` 在偵錯工具中將資訊傳送至傾印裝置，藉此實現。

**相關文章** [atl 教學](../../atl/active-template-library-atl-tutorial.md)課程，[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl：:D 通知

建立資料物件和通知接收之間的連接。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

這可讓通知接收器接收物件中變更的通知。

若要終止連接，請呼叫[DUnadvise](#dunadvise)。

請參閱 Windows SDK 中的[IDataObject：:D 通知](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)。

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl：:D Unadvise

終止先前透過[DAdvise](#dadvise)所建立的連接。

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：:D unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) 。

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl：： EnumDAdvise

建立列舉值以逐一查看目前的諮詢連接。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：： EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) 。

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl：： EnumFormatEtc

建立列舉值，以逐一查看 `FORMATETC` 資料物件所支援的結構。

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：： EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

將變更通知傳送回目前受管理的每個通知接收。

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl：： GetCanonicalFormatEtc

抓取邏輯上 `FORMATETC` 對等結構，使其更複雜。

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：： GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) 。

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl：：操作

將資料從資料物件傳送到用戶端。

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>備註

*PformatetcIn*參數必須指定 TYMED_MFPICT 的儲存媒體類型。

請參閱 Windows SDK 中的[IDataObject：：操作](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)。

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl：： GetDataHere

類似于 `GetData` ，但用戶端必須配置 `STGMEDIUM` 結構。

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：： GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) 。

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

判斷資料物件是否支援 `FORMATETC` 傳送資料的特定結構。

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：： QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) 。

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl：： SetData

將資料從用戶端傳送至資料物件。

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDataObject：： SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) 。

## <a name="see-also"></a>請參閱

[類別概觀](../../atl/atl-class-overview.md)
