---
title: Ipointerinactiveimpl 類別
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326441"
---
# <a name="ipointerinactiveimpl-class"></a>Ipointerinactiveimpl 類別

此類實現`IUnknown`和[IPointer非活動](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)介面方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPointerInactiveImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPointerinactiveimpl::取得啟動策略](#getactivationpolicy)|檢索物件的當前啟動策略。 ATL 實現返回E_NOTIMPL。|
|[指標非活動化::在活動滑鼠移動上](#oninactivemousemove)|通知物件滑鼠指標已移到該物件上,指示該物件可以觸發滑鼠事件。 ATL 實現返回E_NOTIMPL。|
|[Ipointerinactive::oninactiveSet游標](#oninactivesetcursor)|設置非活動物件的滑鼠指標。 ATL 實現返回E_NOTIMPL。|

## <a name="remarks"></a>備註

非活動物件只是載入或運行的物件。 與活動物件不同,非活動物件無法接收 Windows 滑鼠和鍵盤消息。 因此,非活動物件使用的資源較少,並且通常效率更高。

[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)介面允許物件支援最小級別的滑鼠交互,同時保持非活動狀態。 此功能對控件特別有用。

類`IPointerInactiveImpl`只需`IPointerInactive`返回 E_NOTIMPL即可實現這些方法。 但是,它通過在`IUnknown`調試版本中向轉儲設備發送資訊來實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerinactiveimpl::取得啟動策略

檢索物件的當前啟動策略。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IPointerInactive::在](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy)Windows SDK 中獲取啟動策略。

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>指標非活動化::在活動滑鼠移動上

通知物件滑鼠指標已移到該物件上,指示該物件可以觸發滑鼠事件。

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IPointerinactive:在](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove)Windows SDK 中打開活動滑鼠移動。

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>Ipointerinactive::oninactiveSet游標

設置非活動物件的滑鼠指標。

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IPointerinactive::在 Windows SDK 中打開"非活動集游標](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor)"。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
