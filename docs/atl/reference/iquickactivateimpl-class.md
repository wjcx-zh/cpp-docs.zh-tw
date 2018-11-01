---
title: IQuickActivateImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 5dacdd4986580ca665d2199568584faafa8d6699
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560806"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 類別

這個類別會結合成單一呼叫容器的控制項初始化。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IQuickActivateImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|擷取目前的顯示大小，執行的控制項。|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|執行快速的載入的控制項的初始化。|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控制項的容器已指派給它的顯示空間。|

## <a name="remarks"></a>備註

[IQuickActivate](/windows/desktop/api/ocidl/nn-ocidl-iquickactivate)介面可幫助避免延遲載入的控制項，藉由結合在單一呼叫中的初始化時的容器。 `QuickActivate`方法可讓容器傳遞至指標[QACONTAINER](/windows/desktop/api/ocidl/ns-ocidl-tagqacontainer)會保留指標的所有介面控制項的結構需要。 在傳回時，控制權會傳遞回指向[QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol)它自己的介面，可供容器會保留指標的結構。 類別`IQuickActivateImpl`提供的預設實作`IQuickActivate`並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

**相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent

擷取目前的顯示大小，執行的控制項。

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>備註

大小為 完整呈現控制項，並指定以 himetric 為單位。

請參閱[IQuickActivate::GetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) Windows SDK 中。

##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate

執行快速的載入的控制項的初始化。

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>備註

此結構包含所需的控制項和某些環境的屬性值的介面指標。 傳回時，控制權會傳遞指標[QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol)結構，其中包含容器需要，自己介面和其他狀態資訊的指標。

請參閱[IQuickActivate::QuickActivate](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-quickactivate) Windows SDK 中。

##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent

通知控制項的容器已指派給它的顯示空間。

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>備註

大小是以 himetric 為單位來指定。

請參閱[IQuickActivate::SetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
