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
ms.openlocfilehash: c201cf6d9d89ab1a6a8e888deee1be79e5770490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495403"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 類別

這個類別`IUnknown`會執行並提供[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)介面的預設實值。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`ISpecifyPropertyPagesImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|填入已計算的 UUID 值陣列。 每個 UUID 都會對應到其中一個屬性頁的 CLSID, 而其中其中一個可顯示在物件的屬性工作表中。|

## <a name="remarks"></a>備註

[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)介面可讓用戶端取得物件所支援之屬性頁的 clsid 清單。 類別`ISpecifyPropertyPagesImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

> [!NOTE]
>  如果您的物件`ISpecifyPropertyPages`不支援屬性頁, 請勿公開介面。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages

使用可在物件的屬性工作表中顯示之屬性頁的 Clsid, 將[CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid)結構中的陣列填滿。

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>備註

ATL 會使用物件的屬性對應來抓取每個 CLSID。

請參閱 Windows SDK 中的[ISpecifyPropertyPages:: GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) 。

## <a name="see-also"></a>另請參閱

[IPropertyPageImpl 類別](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
