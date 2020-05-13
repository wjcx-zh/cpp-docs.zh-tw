---
title: IDataObjectimpl 類別
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
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329845"
---
# <a name="idataobjectimpl-class"></a>IDataObjectimpl 類別

此類提供支援統一數據傳輸和管理連接的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IDataObjectImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDataObjectimpl::D建議](#dadvise)|在數據物件和通知接收器之間建立連接。 這使建議接收器能夠接收物件中更改的通知。|
|[IDataObjectimpl::D無建議](#dunadvise)|終止以前通過`DAdvise`建立的連接。|
|[IDataObjectimpl::枚舉建議](#enumdadvise)|創建枚舉器以通過當前諮詢連接反覆運算。|
|[IDataObjectimple::枚舉格式](#enumformatetc)|創建枚舉器以迴圈瀏覽數據物件`FORMATETC`支援的結構。 ATL 實現返回E_NOTIMPL。|
|[IDataObjectimpl::火數據更改](#firedatachange)|將更改通知發送回每個通知接收器。|
|[IDataObjectimpl::取得規範格式](#getcanonicalformatetc)|檢索與更複雜的結構在邏輯`FORMATETC`上等效的結構。 ATL 實現返回E_NOTIMPL。|
|[IDataObjectimpl::取得資料](#getdata)|將數據從數據物件傳輸到用戶端。 數據在`FORMATETC`結構中描述,並通過`STGMEDIUM`結構傳輸。|
|[IDataObjectimpl::取得資料在這裡](#getdatahere)|與`GetData`類似 ,但客戶端`STGMEDIUM`必須分配結構。 ATL 實現返回E_NOTIMPL。|
|[IDataObjectimpl::查詢取得資料](#querygetdata)|確定數據物件是否支援用於傳輸數據`FORMATETC`的特定結構。 ATL 實現返回E_NOTIMPL。|
|[IDataObjectimpl::集資料](#setdata)|將數據從用戶端傳輸到數據物件。 ATL 實現返回E_NOTIMPL。|

## <a name="remarks"></a>備註

[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)介面提供了支援統一數據傳輸的方法。 `IDataObject`使用標準格式結構[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)來檢索和存儲數據。

`IDataObject`還管理連接,建議接收器處理數據更改通知。 為了使用戶端從數據物件接收數據更改通知,客戶端必須在稱為建議接收器的對象上實現[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)介面。 當用戶端然後調用`IDataObject::DAdvise`時 ,數據物件和通知接收器之間建立連接。

類`IDataObjectImpl`通過在調試生成中`IDataObject`向 轉`IUnknown`儲設備 發送資訊來提供 和實現的默認實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectimpl::D建議

在數據物件和通知接收器之間建立連接。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

這使建議接收器能夠接收物件中更改的通知。

要終止連線,請致電[DUnadvise](#dunadvise)。

請參閱[IDataObject::D Windows](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) SDK 中的建議。

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectimpl::D無建議

終止以前通過[DAdvise](#dadvise)建立的連接。

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>備註

請參閱[IDataObject::D在](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)Windows SDK 中提供"不建議」。

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectimpl::枚舉建議

創建枚舉器以通過當前諮詢連接反覆運算。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

請參閱[IDataObject::在](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise)Windows SDK 中提供枚舉建議。

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectimple::枚舉格式

創建枚舉器以迴圈瀏覽數據物件`FORMATETC`支援的結構。

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>備註

請參閱[IDataObject::Windows SDK 中的枚舉格式。](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc)

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectimpl::火數據更改

將更改通知發送回當前正在管理的每個通知接收器。

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectimpl::取得規範格式

檢索與更複雜的結構在邏輯`FORMATETC`上等效的結構。

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IDataObject:在](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc)Windows SDK 中獲取規範格式。

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectimpl::取得資料

將數據從數據物件傳輸到用戶端。

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>備註

*pformatetcIn*參數必須指定存儲介質類型的TYMED_MFPICT。

請參閱[IDataObject:獲取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的數據。

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectimpl::取得資料在這裡

與`GetData`類似 ,但客戶端`STGMEDIUM`必須分配結構。

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IDataObject:在](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere)Windows SDK 中獲取數據。

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectimpl::查詢取得資料

確定數據物件是否支援用於傳輸數據`FORMATETC`的特定結構。

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IDataObject::查詢 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) SDK 中的數據獲取數據。

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectimpl::集資料

將數據從用戶端傳輸到數據物件。

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IDataObject:在](/windows/win32/api/objidl/nf-objidl-idataobject-setdata)Windows SDK 中設置數據。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
