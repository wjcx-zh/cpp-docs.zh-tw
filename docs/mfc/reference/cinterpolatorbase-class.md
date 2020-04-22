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
ms.openlocfilehash: efa08aa5dd556d7e136323c31451a9f33bd72ec6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754954"
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
|[C插值器基礎:C插值器基礎](#cinterpolatorbase)|構造`CInterpolatorBase`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C插值器基礎::建立實體](#createinstance)|創建`CInterpolatorBase`的實體並儲存指向自訂插值器的指標,該指標將處理事件。|
|[CInterpolatorBase:取得相依性](#getdependencies)|獲取插值器的依賴項。 (覆寫 `CUIAnimationInterpolatorBase::GetDependencies`。)|
|[C插值器基礎:取得持續時間](#getduration)|獲取插值器的持續時間。 (覆寫 `CUIAnimationInterpolatorBase::GetDuration`。)|
|[C插值器基礎:取得最終值](#getfinalvalue)|獲取插值器引由的最終值。 (覆寫 `CUIAnimationInterpolatorBase::GetFinalValue`。)|
|[C插值器基礎::刑警價值](#interpolatevalue)|插值在給定偏移量處的值(覆`CUIAnimationInterpolatorBase::InterpolateValue`寫 . )|
|[C插值器基礎::刑警組織](#interpolatevelocity)|插值在給定偏移處的速度(覆`CUIAnimationInterpolatorBase::InterpolateVelocity`寫 . )|
|[C插值器基礎:設定自訂器](#setcustominterpolator)|存儲指向自定義插值器的指標,該指標將處理事件。|
|[C插值器基礎::設定持續時間](#setduration)|設定插值器的持續時間(覆`CUIAnimationInterpolatorBase::SetDuration`寫 .)|
|[C插值器基礎::設定初始值和速度](#setinitialvalueandvelocity)|設置插值器的初始值和速度。 (覆寫 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。)|

## <a name="remarks"></a>備註

當`IUIAnimationTransitionFactory::CreateTransition``CCustomTransition`對物件作為動畫初始化過程的一部分(由`CAnimationController::AnimateGroup`啟動) 創建並傳遞給該處理程式時, 通常不需要直接使用此類,它只是將所有事件傳遞給`CCustomInterpolator`派生類,其指標傳遞給`CCustomTransition`的構造函數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>C插值器基礎:C插值器基礎

構造 C插值器基礎物件。

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>C插值器基礎::建立實體

創建 CInterpolatorBase 的實體並儲存指向自訂插值器的指標,該指標將處理事件。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>參數

*p插值器*<br/>
指向自定義插值器的指標。

*普漢德勒*<br/>
輸出。 當函數返回時,包含指向 CInterpolatorBase 實例的指標。

### <a name="return-value"></a>傳回值

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase:取得相依性

獲取插值器的依賴項。

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>參數

*初始價值相依性*<br/>
輸出。 插值器的一些方面,這些插值取決於傳遞給 Set初始值和Velocity 的初始值。

*初始速度相依性*<br/>
輸出。 插值器的方面,這些插值器取決於傳遞給 Set 初始值和Velocity的初始速度。

*持續時間 相依*<br/>
輸出。 插值器的一些方面,這些插值器取決於傳遞給 SetDuration 的持續時間。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,則返回E_FAIL,或者自定義實現從 GetDependencies 方法返回 FALSE。

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>C插值器基礎:取得持續時間

獲取插值器的持續時間。

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>參數

*duration*<br/>
輸出。 轉換的持續時間,以秒為單位。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,則返回E_FAIL,或者自定義實現從 GetDuration 方法返回 FALSE。

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>C插值器基礎:取得最終值

獲取插值器引由的最終值。

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>參數

*value*<br/>
輸出。 轉換結束時變數的最終值。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,則返回E_FAIL,或者自定義實現從 GetFinalValue 方法返回 FALSE。

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>C插值器基礎::刑警價值

插值在給定偏移量處的值

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>參數

*位移*<br/>
轉換開始時的偏移量。 偏移量始終大於或等於零,小於轉換的持續時間。 如果轉換的持續時間為零,則不調用此方法。

*value*<br/>
輸出。 插值值。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,或者自定義實現從插值值方法返回 FALSE,則返回E_FAIL。

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>C插值器基礎::刑警組織

在給定位移插入速度

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>參數

*位移*<br/>
轉換開始時的偏移量。 偏移量始終大於或等於零,小於或等於轉換的持續時間。 如果轉換的持續時間為零,則不調用此方法。

*velocity*<br/>
輸出。 偏移處變數的速度。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,或者自定義實現從插值速度方法返回 FALSE,則返回E_FAIL。

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>C插值器基礎:設定自訂器

存儲指向自定義插值器的指標,該指標將處理事件。

```cpp
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>參數

*p插值器*<br/>
指向自定義插值器的指標。

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>C插值器基礎::設定持續時間

設定插值器的持續時間

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,或者自定義實現從 SetDuration 方法返回 FALSE,則返回E_FAIL。

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>C插值器基礎::設定初始值和速度

設置插值器的初始值和速度。

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>參數

*初始值*<br/>
轉換開始時變數的值。

*初始速度*<br/>
轉換開始時變數的速度。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 如果未設置 CCustomInterpolator,則傳回E_FAIL,或者自訂實現從 Set初始值和Velocity 方法返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
