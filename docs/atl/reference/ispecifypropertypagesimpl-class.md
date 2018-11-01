---
title: ISpecifyPropertyPagesImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: fcabbcd2d5977a28f46b3d8ebfc47e8fd978f3cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470771"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 類別

這個類別會實作`IUnknown`，並提供的預設實作[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages)介面。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`ISpecifyPropertyPagesImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|填滿計算 UUID 的陣列值。 每個 UUID 會對應至其中一個可顯示物件的屬性工作表中的屬性頁的 CLSID。|

## <a name="remarks"></a>備註

[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages)介面可讓用戶端取得物件所支援的屬性頁 Clsid 的清單。 類別`ISpecifyPropertyPagesImpl`提供此介面的預設實作，並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

> [!NOTE]
>  不會公開`ISpecifyPropertyPages`介面，如果您的物件不支援屬性頁。

**相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

填入陣列[CAUUID](/windows/desktop/api/ocidl/ns-ocidl-tagcauuid)結構可以顯示物件的屬性工作表中之屬性頁面的 Clsid。

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應，來擷取每個 CLSID。

請參閱[ISpecifyPropertyPages::GetPages](/windows/desktop/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[IPropertyPageImpl 類別](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
