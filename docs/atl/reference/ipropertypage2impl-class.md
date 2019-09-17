---
title: IPropertyPage2Impl 類別
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495600"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl 類別

這個類別`IUnknown`會執行並繼承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的預設實值。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPropertyPage2Impl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|指定當屬性頁啟動時，哪一個屬性控制項將接收焦點。 ATL 執行會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

[IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2)介面會藉 `EditProperty`由新增方法來擴充 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)。 這個方法可讓用戶端選取屬性頁物件中的特定屬性。

類別`IPropertyPage2Impl`只會傳回的`IPropertyPage2::EditProperty`E_NOTIMPL。 不過，它會繼承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的預設執行，並`IUnknown`在偵錯工具中將資訊傳送至傾印裝置來實現。

當您建立屬性頁時，您的類別通常是衍生`IPropertyPageImpl`自。 若要提供的額外支援`IPropertyPage2`，請修改您的類別定義， `EditProperty`並覆寫方法。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程，[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="editproperty"></a>IPropertyPage2Impl::EditProperty

指定當屬性頁啟動時，哪一個屬性控制項將接收焦點。

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage2：： EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) 。

## <a name="see-also"></a>另請參閱

[IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
