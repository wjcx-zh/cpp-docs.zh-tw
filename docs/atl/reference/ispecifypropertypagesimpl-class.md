---
title: I 指定屬性頁頁類別
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
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326404"
---
# <a name="ispecifypropertypagesimpl-class"></a>I 指定屬性頁頁類別

此類實現`IUnknown`並提供[ISpecify PropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)介面的預設實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`ISpecifyPropertyPagesImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 指定屬性頁頁面:取得頁面](#getpages)|填充 UUID 值的計陣陣組。 每個 UUID 對應於可在物件的屬性表中顯示的屬性頁之一的 CLSID。|

## <a name="remarks"></a>備註

[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)介面允許客戶端取得物件支援的屬性頁的 CLSID 的清單。 類`ISpecifyPropertyPagesImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

> [!NOTE]
> 如果物件不支援屬性`ISpecifyPropertyPages`頁,則不要公開介面。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>I 指定屬性頁頁面:取得頁面

使用可在物件的屬性表中顯示的屬性頁的 CLSID 填充[CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid)結構中的陣列。

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>備註

ATL 使用物件的屬性映射檢索每個 CLSID。

請參閱[I 指定屬性頁:獲取](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages)Windows SDK 中的頁面。

## <a name="see-also"></a>另請參閱

[IPropertypageimpl 類別](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerProperty 瀏覽類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
