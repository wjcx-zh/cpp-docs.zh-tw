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
ms.openlocfilehash: 2169686ebbf756c5caf9232f5031532c62ac8265
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495513"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 類別

這個類別會將容器的控制項初始化結合成單一呼叫。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IQuickActivateImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|抓取正在執行之控制項的目前顯示大小。|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|執行要載入之控制項的快速初始化。|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控制項容器已指派多少顯示空間。|

## <a name="remarks"></a>備註

[IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate)介面可協助容器在單一呼叫中結合初始化，以避免載入控制項時的延遲。 方法可讓容器將指標傳遞至 [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) 結構，以保留控制項所需之所有介面的指標。`QuickActivate` 在傳回時，控制項會將指標回傳至[QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol)結構，其會保留指向其本身介面的指標，由容器使用。 類別`IQuickActivateImpl`會提供的預設`IQuickActivate`執行，並`IUnknown`在偵錯工具中將資訊傳送至傾印裝置，藉此實現。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程，[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

抓取正在執行之控制項的目前顯示大小。

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>備註

大小適用于控制項的完整轉譯，並以 HIMETRIC 單位指定。

請參閱 Windows SDK 中的[IQuickActivate：： GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) 。

##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

執行要載入之控制項的快速初始化。

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>備註

結構包含控制項所需介面的指標，以及某些環境屬性的值。 傳回時，控制項會將指標傳遞至[QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol)結構，其中包含容器所需之本身介面的指標，以及其他狀態資訊。

請參閱 Windows SDK 中的[IQuickActivate：： QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) 。

##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

通知控制項容器已指派多少顯示空間。

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>備註

大小是以 HIMETRIC 單位來指定。

請參閱 Windows SDK 中的[IQuickActivate：： SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) 。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
