---
title: IPointerInactiveImpl 類別
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
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495660"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 類別

這個類別`IUnknown`會執行和[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)介面方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPointerInactiveImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|抓取物件的目前啟用原則。 ATL 執行會傳回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|通知物件滑鼠指標已移至其上方, 表示物件可以引發滑鼠事件。 ATL 執行會傳回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|設定非作用中物件的滑鼠指標。 ATL 執行會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

非作用中的物件是單純載入或執行中的物件。 與作用中物件不同的是, 非使用中物件無法接收 Windows 滑鼠和鍵盤訊息。 因此, 非作用中的物件會使用較少的資源, 而且通常會更有效率。

[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)介面可讓物件支援最小層級的滑鼠互動, 同時保持非使用中狀態。 此功能特別適用于控制項。

類別`IPointerInactiveImpl`會藉由直接傳回 E_NOTIMPL 來執行方法。`IPointerInactive` 不過, 它會`IUnknown`藉由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

抓取物件的目前啟用原則。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPointerInactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) 。

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

通知物件滑鼠指標已移至其上方, 表示物件可以引發滑鼠事件。

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPointerInactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) 。

##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

設定非作用中物件的滑鼠指標。

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPointerInactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) 。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
