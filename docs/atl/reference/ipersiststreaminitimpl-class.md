---
title: Ipersiststreaminitimpl<ccomspy> 類別
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 7a350a4349cb825795a18dd860a2482952b04dcb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496144"
---
# <a name="ipersiststreaminitimpl-class"></a>Ipersiststreaminitimpl<ccomspy> 類別

這個類別`IUnknown`會執行並提供[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面的預設實值。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPersistStreamInitImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|抓取物件的 CLSID。|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|抓取儲存物件資料所需的資料流程大小。 ATL 執行會傳回 E_NOTIMPL。|
|[IPersistStreamInitImpl::InitNew](#initnew)|初始化新建立的物件。|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|檢查物件的資料自從上次儲存之後是否已變更。|
|[IPersistStreamInitImpl::Load](#load)|從指定的資料流程載入物件的屬性。|
|[IPersistStreamInitImpl::Save](#save)|將物件的屬性儲存至指定的資料流程。|

## <a name="remarks"></a>備註

[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面可讓用戶端要求您的物件載入, 並將其持續性資料儲存至單一資料流程。 類別`IPersistStreamInitImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getclassid"></a>Ipersiststreaminitimpl<ccomspy>:: GetClassID

抓取物件的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 。

##  <a name="getsizemax"></a>Ipersiststreaminitimpl<ccomspy>:: GetSizeMax

抓取儲存物件資料所需的資料流程大小。

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) 。

##  <a name="initnew"></a>Ipersiststreaminitimpl<ccomspy>:: InitNew

初始化新建立的物件。

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) 。

##  <a name="isdirty"></a>Ipersiststreaminitimpl<ccomspy>:: IsDirty

檢查物件的資料自從上次儲存之後是否已變更。

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersistStreamInit:: IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) 。

##  <a name="load"></a>Ipersiststreaminitimpl<ccomspy>:: Load

從指定的資料流程載入物件的屬性。

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應來抓取此資訊。

請參閱 Windows SDK 中的[IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) 。

##  <a name="save"></a>Ipersiststreaminitimpl<ccomspy>:: Save

將物件的屬性儲存至指定的資料流程。

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應來儲存此資訊。

請參閱 Windows SDK 中的[IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) 。

## <a name="see-also"></a>另請參閱

[儲存體和串流](/windows/win32/Stg/storages-and-streams)<br/>
[類別總覽](../../atl/atl-class-overview.md)
