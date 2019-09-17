---
title: IProvideClassInfo2Impl 類別
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
ms.openlocfilehash: f0ff3607002d32b4e21f7fc2199cc5da3662af8b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495533"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl 類別

這個類別會提供[IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)和[iprovideclassinfo2.getguid](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)方法的預設執行。

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

*pcoclsid*<br/>
Coclass 識別碼的指標。

*psrcid*<br/>
Coclass 的預設外送分配介面識別碼指標。

*plibid*<br/>
類型程式庫之 LIBID 的指標，其中包含介面的相關資訊。 根據預設，會傳遞伺服器層級類型程式庫。

*wMajor*<br/>
類型程式庫的主要版本。 預設值為 1。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*tihclass*<br/>
用來管理 coclass 類型資訊的類別。 預設值為 `CComTypeInfoHolder`。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|說明|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|抓取 coclass 類型資訊的指標。`ITypeInfo`|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|抓取物件之傳出分配介面的 GUID。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|管理 coclass 的類型資訊。|

## <a name="remarks"></a>備註

[Iprovideclassinfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2).getguid介面會藉 `GetGUID`由新增方法來擴充 [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)。 這個方法可讓用戶端抓取物件的輸出介面 IID，以取得其預設事件集。 類別`IProvideClassInfo2Impl`提供`IProvideClassInfo`和方法的預設執行。`IProvideClassInfo2`

`IProvideClassInfo2Impl`包含類型`CComTypeInfoHolder`的靜態成員，它會管理 coclass 的類型資訊。

## <a name="inheritance-hierarchy"></a>繼承階層

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo

抓取 coclass 類型資訊的指標。`ITypeInfo`

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IProvideClassInfo：： GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) 。

##  <a name="getguid"></a>IProvideClassInfo2Impl：： GetGUID

抓取物件之傳出分配介面的 GUID。

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[iprovideclassinfo2.getguid：： GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) 。

##  <a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

建構函式。

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>備註

在`AddRef` [_tih](#_tih)成員上呼叫。 此解構函式會呼叫 `Release`。

##  <a name="_tih"></a>IProvideClassInfo2Impl::_tih

這個靜態資料成員是類別樣板參數*tihclass*的實例，預設為`CComTypeInfoHolder`。

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>備註

`_tih`管理 coclass 的類型資訊。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
