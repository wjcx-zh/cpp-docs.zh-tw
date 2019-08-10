---
title: CAnimationManagerEventHandler 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: bd13ba4d0dd60f65372b2c1f51d70d338566301e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916251"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler 類別

實作回呼，當動畫管理員的狀態變更時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|建構 `CAnimationManagerEventHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|建立物件的`CAnimationManagerEventHandler`實例。|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|當動畫管理員的狀態變更時呼叫。 (覆寫 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|儲存動畫控制器的指標以路由事件。|

## <a name="remarks"></a>備註

當您呼叫 CAnimationController:: EnableAnimationManagerEvent 時, 會建立此事件處理常式並將它傳遞至 IUIAnimationManager:: SetManagerEventHandler 方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler:: CAnimationManagerEventHandler

必須有 Visual Studio 2010 SP1。

結構 CAnimationManagerEventHandler 物件。

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>CAnimationManagerEventHandler:: CreateInstance

必須有 Visual Studio 2010 SP1。

建立 CAnimationManagerEventHandler 物件的實例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器的指標, 會接收事件。

*ppManagerEventHandler*<br/>
輸出. 如果此方法成功, 它會包含 COM 物件的指標, 該物件將會處理動畫管理員的狀態更新。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 否則, 它會傳回 HRESULT 錯誤碼。

##  <a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler:: OnManagerStatusChanged

必須有 Visual Studio 2010 SP1。

當動畫管理員的狀態變更時呼叫。

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>參數

*newStatus*<br/>
新狀態。

*previousStatus*<br/>
先前的狀態。

### <a name="return-value"></a>傳回值

目前的實值一律會傳回 S_OK;

##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController

必須有 Visual Studio 2010 SP1。

儲存動畫控制器的指標以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*pAnimationController*<br/>
動畫控制器的指標, 會接收事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
