---
title: IPerPropertyBrowsingImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: 263f6826ac921d864dee646ef063c8b456b00af1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495720"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 類別

這個類別`IUnknown`會執行並允許用戶端存取物件屬性頁中的資訊。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPerPropertyBrowsingImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|抓取描述指定屬性的字串。|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|抓取字串陣列, 其對應于指定屬性可接受的值。|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|抓取 VARIANT, 其中包含指定的 DISPID 所識別之屬性的值。 DISPID 與取自的字串名稱`GetPredefinedStrings`相關聯。 ATL 執行會傳回 E_NOTIMPL。|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|抓取與指定屬性相關聯之屬性頁的 CLSID。|

## <a name="remarks"></a>備註

[IPerPropertyBrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing)介面可讓用戶端存取物件屬性頁中的資訊。 類別`IPerPropertyBrowsingImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

> [!NOTE]
>  如果您使用 Microsoft Access 作為容器應用程式, 您必須從`IPerPropertyBrowsingImpl`衍生類別。 否則, Access 將不會載入您的控制項。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString

抓取描述指定屬性的字串。

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPerPropertyBrowsing:: GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) 。

##  <a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings

以零個專案填滿每個陣列。

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>傳回值

ATL 的[GetPredefinedValue](#getpredefinedvalue)的執行會傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPerPropertyBrowsing:: GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) 。

##  <a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue

抓取 VARIANT, 其中包含指定的 DISPID 所識別之屬性的值。 DISPID 與取自的字串名稱`GetPredefinedStrings`相關聯。

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

ATL 的[GetPredefinedStrings](#getpredefinedstrings)的執行會抓取沒有對應的字串。

請參閱 Windows SDK 中的[IPerPropertyBrowsing:: GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) 。

##  <a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage

抓取與指定屬性相關聯之屬性頁的 CLSID。

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應來取得此資訊。

請參閱 Windows SDK 中的[IPerPropertyBrowsing:: MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) 。

## <a name="see-also"></a>另請參閱

[IPropertyPageImpl 類別](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
