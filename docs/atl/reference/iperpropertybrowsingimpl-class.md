---
title: IPerProperty 瀏覽類別
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
ms.openlocfilehash: f8fb80cc38e775b9b26afa033647faac694e968a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326507"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerProperty 瀏覽類別

此類實現`IUnknown`並允許用戶端訪問對象的屬性頁中的資訊。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPerPropertyBrowsingImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPer屬性瀏覽::取得顯示字串](#getdisplaystring)|檢索描述給定屬性的字串。|
|[IPerProperty 瀏覽::取得預定義的字串](#getpredefinedstrings)|檢索與給定屬性可以接受的值對應的字串陣列。|
|[IPerProperty 流覽::獲取預定義價值](#getpredefinedvalue)|檢索包含給定 DISPID 識別的屬性的值的 VARIANT。 DISPID 與`GetPredefinedStrings`從 檢索到的字串名稱相關聯。 ATL 實現返回E_NOTIMPL。|
|[IPer屬性瀏覽::映射屬性頁](#mappropertytopage)|檢索與給定屬性關聯的屬性頁的 CLSID。|

## <a name="remarks"></a>備註

[IPerProperty 流覽](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing)介面允許用戶端訪問物件屬性頁中的資訊。 類`IPerPropertyBrowsingImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

> [!NOTE]
> 如果使用 Microsoft Access 作為容器應用程式,`IPerPropertyBrowsingImpl`則必須從 派生類。 否則,Access將不會載入您的控制項。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>IPer屬性瀏覽::取得顯示字串

檢索描述給定屬性的字串。

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>備註

請參閱[IPer 屬性流覽::在](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring)Windows SDK 中獲取顯示字串。

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerProperty 瀏覽::取得預定義的字串

用零項填充每個陣列。

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>傳回值

ATL 對[GetPreValue 的](#getpredefinedvalue)實現E_NOTIMPL回報。

### <a name="remarks"></a>備註

請參閱[IPer 屬性流覽::在](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings)Windows SDK 中獲取預定義的字串。

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerProperty 流覽::獲取預定義價值

檢索包含給定 DISPID 識別的屬性的值的 VARIANT。 DISPID 與`GetPredefinedStrings`從 檢索到的字串名稱相關聯。

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

ATL 的[GetPre 定義字串](#getpredefinedstrings)的實現不會檢索相應的字串。

請參閱[IPerProperty 流覽::在](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue)Windows SDK 中獲取預定義值。

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>IPer屬性瀏覽::映射屬性頁

檢索與指定屬性關聯的屬性頁的 CLSID。

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>備註

ATL 使用物件的屬性映射來獲取此資訊。

請參考[IPer 屬性瀏覽::Windows SDK 中的映射屬性到頁面](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage)。

## <a name="see-also"></a>另請參閱

[IPropertypageimpl 類別](../../atl/reference/ipropertypageimpl-class.md)<br/>
[I 指定屬性頁頁類別](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
