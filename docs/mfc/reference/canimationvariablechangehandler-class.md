---
title: CAnimationVariableChangeHandler 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 7f45fdad00bacf56e2ee8c30b76e99d626902534
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377090"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler 類別

實作回呼，當動畫變數的值變更時由動畫 API 呼叫。

## <a name="syntax"></a>語法

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|建構 `CAnimationVariableChangeHandler` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|創建`CAnimationVariableChangeHandler`物件的實例。|
|[C 動畫可變更處理程式::在值轉換](#onvaluechanged)|當動畫變數的值已更改時調用。 (覆寫 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`。)|
|[動畫變數變更處理程式::設定動畫控制器](#setanimationcontroller)|存儲指向動畫控制器的指標以路由事件。|

## <a name="remarks"></a>備註

此事件處理程式在調用`IUIAnimationVariable::SetVariableChangeHandler``CAnimationVariable::EnableValueChangedEvent``CAnimationBaseObject::EnableValueChangedEvent`或 時創建並傳遞給方法(這啟用動畫物件中封裝的所有動畫變數的此事件)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a>C 動畫可變更處理程式::在值轉換

當動畫變數的值已更改時調用。

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>參數

*文稿*<br/>
為變數設置動畫的情節提要。

*變動*<br/>
已更新的動畫變數。

*newValue*<br/>
新的值。

*前一個值*<br/>
上一個值。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>動畫變數變更處理程式::設定動畫控制器

存儲指向動畫控制器的指標以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>參數

*動畫控制器*<br/>
指向動畫控制器的指標,該控制器將接收事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
