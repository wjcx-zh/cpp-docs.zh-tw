---
title: IPropertypage2Impl 類
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
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329597"
---
# <a name="ipropertypage2impl-class"></a>IPropertypage2Impl 類

此類實現`IUnknown`並繼承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的預設實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPropertyPage2Impl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPropertypage2impl::編輯屬性](#editproperty)|指定啟動屬性頁時,哪個屬性控制項將接收焦點。 ATL 實現返回E_NOTIMPL。|

## <a name="remarks"></a>備註

[IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2)介面通過`EditProperty`添加 方法擴展[IPropertyPage。](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) 此方法允許用戶端在屬性頁物件中選擇特定屬性。

類別`IPropertyPage2Impl`只是傳`IPropertyPage2::EditProperty`回E_NOTIMPL 。 但是,它繼承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的預設實現,`IUnknown`並通過 在調試版本中向轉儲設備發送信息實現。

建立屬性頁時,類別通常派生自`IPropertyPageImpl`。 要提供`IPropertyPage2`的額外支援,請修改類別定義並重寫 該`EditProperty`方法 。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPropertyPage`

[I 屬性頁頁](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertypage2impl::編輯屬性

指定啟動屬性頁時,哪個屬性控制項將接收焦點。

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IPropertyPage2:編輯](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty)Windows SDK 中的屬性。

## <a name="see-also"></a>另請參閱

[IPerProperty 瀏覽類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[I 指定屬性頁頁類別](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
