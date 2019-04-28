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
ms.openlocfilehash: d7d9f048fceb3a569b024d7fe2b87f30a828b68e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274824"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 類別

這個類別會實作`IUnknown`而[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive)介面方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IPointerInactiveImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|擷取目前啟用的原則物件。 ATL 實作會傳回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|將滑鼠指標已移至其上方，表示物件的物件可以引發滑鼠事件的通知。 ATL 實作會傳回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|設定滑鼠指標為非作用中的物件。 ATL 實作會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

另一個則是只要載入或執行非使用中的物件。 不同於作用中的物件，非作用中的物件無法接收 Windows 滑鼠和鍵盤訊息。 因此，非作用中的物件會使用較少的資源，並且通常更有效率。

[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive)介面允許支援滑鼠互動，同時維持非使用中的最低層級物件。 這項功能是特別有用的控制項。

類別`IPointerInactiveImpl`實作`IPointerInactive`藉由只傳回 E_NOTIMPL 的方法。 不過，它會實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

**相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

擷取目前啟用的原則物件。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IPointerInactive::GetActivationPolicy](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) Windows SDK 中。

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

將滑鼠指標已移至其上方，表示物件的物件可以引發滑鼠事件的通知。

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

請參閱[IPointerInactive::OnInactiveMouseMove](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) Windows SDK 中。

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

設定滑鼠指標為非作用中的物件。

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

請參閱[IPointerInactive::OnInactiveSetCursor](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
