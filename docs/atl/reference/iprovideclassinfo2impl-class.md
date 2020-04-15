---
title: I提供ClassInfo2Impl類
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329562"
---
# <a name="iprovideclassinfo2impl-class"></a>I提供ClassInfo2Impl類

此類提供[IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)和[IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)方法的預設實現。

## <a name="syntax"></a>語法

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>參數

*普科克勞西德*<br/>
指向同類標識符的指標。

*psrcid*<br/>
指向共類默認傳出介面的標識符的指標。

*普利比德*<br/>
指向類型庫 LIBID 的指標,其中包含有關介面的資訊。 預設情況下,傳遞伺服器級類型庫。

*w 主要*<br/>
類型程式庫的主要版本。 預設值為 1。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*提赫班*<br/>
用於管理共類類型資訊的類。 預設值是 `CComTypeInfoHolder`。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|----------|-----------------|
|[I提供類資訊2impl::i提供類資訊2impl](#iprovideclassinfo2impl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I提供類別資訊2Impl::取得類資訊](#getclassinfo)|檢索指向同`ITypeInfo`類類型信息的指標。|
|[I提供類別資訊2impl::取得GUID](#getguid)|檢索物件傳出的 dispinterface 的 GUID。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[I提供ClassInfo2Impl::_tih](#_tih)|管理共類的類型資訊。|

## <a name="remarks"></a>備註

[IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)介面透過`GetGUID`新增方法擴展[IProvideClassInfo。](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) 此方法允許用戶端為其預設事件集檢索物件的傳出介面 IID。 類`IProvideClassInfo2Impl`提供和`IProvideClassInfo``IProvideClassInfo2`方法的預設實現。

`IProvideClassInfo2Impl`包含管理 coclass`CComTypeInfoHolder`的類型 資訊的類型靜態成員。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>I提供類別資訊2Impl::取得類資訊

檢索指向同`ITypeInfo`類類型信息的指標。

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

請參閱[I 提供類資訊:在](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo)Windows SDK 中獲取類資訊。

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>I提供類別資訊2impl::取得GUID

檢索物件傳出的 dispinterface 的 GUID。

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>備註

請參閱[I提供ClassInfo2:在](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid)Windows SDK 中獲取GUID。

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>I提供類資訊2impl::i提供類資訊2impl

建構函式。

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>備註

調用`AddRef`[_tih](#_tih)成員。 此解構函式會呼叫 `Release`。

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>I提供ClassInfo2Impl::_tih

此靜態資料成員是類別參數*tihclass*的實體,預設情況下是`CComTypeInfoHolder`。

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>備註

`_tih`管理共類的類型資訊。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
