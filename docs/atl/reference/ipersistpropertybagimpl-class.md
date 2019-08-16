---
title: IPersistPropertyBagImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: 15b9c9738d921c4c6f7837f9280c6dd6b09392d6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495769"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 類別

這個類別`IUnknown`會執行並允許物件將其屬性儲存至用戶端提供的屬性包。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPersistPropertyBagImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|抓取物件的 CLSID。|
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新建立的物件。 ATL 實作為傳回 S_OK。|
|[IPersistPropertyBagImpl::Load](#load)|從用戶端提供的屬性包載入物件的屬性。|
|[IPersistPropertyBagImpl::Save](#save)|將物件的屬性儲存至用戶端提供的屬性包。|

## <a name="remarks"></a>備註

[IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\))介面可讓物件將其屬性儲存至用戶端提供的屬性包。 類別`IPersistPropertyBagImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

`IPersistPropertyBag`與[IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\))和[IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\))搭配運作。 後面兩個介面必須由用戶端執行。 透過`IPropertyBag`, 用戶端會儲存並載入物件的個別屬性。 透過`IErrorLog`, 物件和用戶端都可以報告遇到的任何錯誤。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID

抓取物件的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 。

##  <a name="initnew"></a>IPersistPropertyBagImpl:: InitNew

初始化新建立的物件。

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersistPropertyBag:: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) 。

##  <a name="load"></a>IPersistPropertyBagImpl:: Load

從用戶端提供的屬性包載入物件的屬性。

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應來抓取此資訊。

請參閱 Windows SDK 中的[IPersistPropertyBag:: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) 。

##  <a name="save"></a>IPersistPropertyBagImpl:: Save

將物件的屬性儲存至用戶端提供的屬性包。

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應來儲存此資訊。 根據預設, 不論*fSaveAllProperties*的值為何, 這個方法都會儲存所有屬性。

請參閱 Windows SDK 中的[IPersistPropertyBag:: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) 。

## <a name="see-also"></a>另請參閱

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[類別總覽](../../atl/atl-class-overview.md)
