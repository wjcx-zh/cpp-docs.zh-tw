---
title: CInterpolatorBase 類別
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916206"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase 類別

實作回呼，當動畫 API 必須計算動畫變數的新值時由此 API 呼叫。

## <a name="syntax"></a>語法

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|`CInterpolatorBase`結構物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|建立的`CInterpolatorBase`實例, 並儲存自訂插即用的指標, 這將會處理事件。|
|[CInterpolatorBase::GetDependencies](#getdependencies)|取得插即用的相依性。 (覆寫 `CUIAnimationInterpolatorBase::GetDependencies`。)|
|[CInterpolatorBase::GetDuration](#getduration)|取得插即用的持續時間。 (覆寫 `CUIAnimationInterpolatorBase::GetDuration`。)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|取得插轉所潛在的最終值。 (覆寫 `CUIAnimationInterpolatorBase::GetFinalValue`。)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|在指定的位移 (覆寫`CUIAnimationInterpolatorBase::InterpolateValue`) 上插上值。|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|在指定的位移 (覆寫`CUIAnimationInterpolatorBase::InterpolateVelocity`) 上插上速度。|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|儲存自訂插即用的指標, 這將會處理事件。|
|[CInterpolatorBase::SetDuration](#setduration)|設定插即用的持續時間`CUIAnimationInterpolatorBase::SetDuration`(覆寫)。|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|設定插即用的初始值和速度。 (覆寫 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。)|

## <a name="remarks"></a>備註

當物件是在動畫初始化程式`IUIAnimationTransitionFactory::CreateTransition` (由`CAnimationController::AnimateGroup`啟動) 中建立時, 會建立此處理程式並將其傳遞給。 `CCustomTransition` 通常您不需要直接使用這個類別, 它只會將所有事件 routs 至`CCustomInterpolator`衍生的類別, 其指標會傳遞至`CCustomTransition`的函式。

## <a name="inheritance-hierarchy"></a>繼承階層

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>CInterpolatorBase:: CInterpolatorBase

結構 CInterpolatorBase 物件。

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>CInterpolatorBase:: CreateInstance

建立 CInterpolatorBase 的實例, 並儲存自訂插即用的指標, 這將會處理事件。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>參數

*pInterpolator*<br/>
自訂插即用的指標。

*ppHandler*<br/>
輸出. 當函式傳回時, 包含 CInterpolatorBase 實例的指標。

### <a name="return-value"></a>傳回值

##  <a name="getdependencies"></a>CInterpolatorBase:: GetDependencies

取得插即用的相依性。

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>參數

*initialValueDependencies*<br/>
輸出. 插上的各個層面, 取決於傳遞至 SetInitialValueAndVelocity 的初始值。

*initialVelocityDependencies*<br/>
輸出. 插上的各個層面取決於傳遞至 SetInitialValueAndVelocity 的初始速度。

*durationDependencies*<br/>
輸出. 插上的各個層面取決於傳遞至 SetDuration 的持續時間。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 GetDependencies 方法傳回 FALSE。

##  <a name="getduration"></a>CInterpolatorBase:: GetDuration

取得插即用的持續時間。

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>參數

*duration*<br/>
輸出. 轉換的持續時間 (以秒為單位)。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 GetDuration 方法傳回 FALSE。

##  <a name="getfinalvalue"></a>CInterpolatorBase:: GetFinalValue

取得插轉所潛在的最終值。

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>參數

*value*<br/>
輸出. 在轉換結束時的最後一個變數值。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 GetFinalValue 方法傳回 FALSE。

##  <a name="interpolatevalue"></a>CInterpolatorBase:: InterpolateValue

在指定的位移上插補值

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>參數

*offset*<br/>
從轉換開始算起的位移。 位移一律大於或等於零, 而且小於轉換的持續時間。 如果轉換的持續時間為零, 則不會呼叫這個方法。

*value*<br/>
輸出. 插補值。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 InterpolateValue 方法傳回 FALSE。

##  <a name="interpolatevelocity"></a>CInterpolatorBase:: InterpolateVelocity

在指定的位移上插補速度

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>參數

*offset*<br/>
從轉換開始算起的位移。 位移一律大於或等於零, 而且小於或等於轉換的持續時間。 如果轉換的持續時間為零, 則不會呼叫這個方法。

*velocity*<br/>
輸出. 變數在位移的速度。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 InterpolateVelocity 方法傳回 FALSE。

##  <a name="setcustominterpolator"></a>CInterpolatorBase:: SetCustomInterpolator

儲存自訂插即用的指標, 這將會處理事件。

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>參數

*pInterpolator*<br/>
自訂插即用的指標。

##  <a name="setduration"></a>CInterpolatorBase:: SetDuration

設定插器的持續時間

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 SetDuration 方法傳回 FALSE。

##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase:: SetInitialValueAndVelocity

設定插即用的初始值和速度。

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>參數

*initialValue*<br/>
轉換開始時的變數值。

*initialVelocity*<br/>
轉換開始時的變數速度。

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回 S_OK。 如果未設定 CCustomInterpolator, 則會傳回 E_FAIL, 或自訂執行會從 SetInitialValueAndVelocity 方法傳回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
