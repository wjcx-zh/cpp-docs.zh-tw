---
title: I快速啟動類別
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
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329559"
---
# <a name="iquickactivateimpl-class"></a>I快速啟動類別

此類將容器的控制初始化合併為單個調用。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IQuickActivateImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I快速啟動::取得內容範圍](#getcontentextent)|檢索正在運行的控制項的當前顯示大小。|
|[I 快速啟動::快速啟動](#quickactivate)|對正在載入的控制項執行快速初始化。|
|[I快速啟動::設定內容範圍](#setcontentextent)|通知容器為其分配的顯示空間的控制項。|

## <a name="remarks"></a>備註

[IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate)介面通過在單個調用中合併初始化,説明容器在載入控制項時避免延遲。 該方法`QuickActivate`允許容器傳遞指向[QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer)結構的指標,該結構包含指向控制項需要的所有介面的指標。 返回時,控件將指標傳回到[QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol)結構,該結構保存指向容器使用的指向其自身介面的指標。 類`IQuickActivateImpl`通過在調試生成中`IQuickActivate`向 轉`IUnknown`儲設備 發送資訊來提供 和實現的默認實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>I快速啟動::取得內容範圍

檢索正在運行的控制項的當前顯示大小。

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>備註

大小用於控制項的完整渲染,並在 HIMETRIC 單位中指定。

請參閱[IQuickActivate:在](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent)Windows SDK 中獲取內容範圍。

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>I 快速啟動::快速啟動

對正在載入的控制項執行快速初始化。

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>備註

結構包含指向控制項所需的介面的指標和某些環境屬性的值。 返回后,控件傳遞指向[QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol)結構的指標,該結構包含指向容器所需的其自身介面的指標和其他狀態資訊。

請參閱[IQuickActivate::](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate)在 Windows SDK 中快速啟動。

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>I快速啟動::設定內容範圍

通知容器為其分配的顯示空間的控制項。

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>備註

大小以 HIMETRIC 單位指定。

請參閱[IQuickActivate:在](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent)Windows SDK 中設置內容範圍。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
