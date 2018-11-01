---
title: CCustomInterpolator 類別
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 49685d079e367449ee5973ab37f0bbc7ea44da14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431899"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator 類別

實作基本 Interpolator。

## <a name="syntax"></a>語法

```
class CCustomInterpolator;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|多載。 建構自訂 interpolator 物件並初始化期間以及指定的值的速度。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCustomInterpolator::GetDependencies](#getdependencies)|取得 interpolator 的相依性。|
|[CCustomInterpolator::GetDuration](#getduration)|取得 interpolator 的持續時間。|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|取得 interpolator 潛在客戶的最後一個值。|
|[CCustomInterpolator::Init](#init)|初始化期間以及最終的值。|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|進行插補在指定的位移值。|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|指定位移處的速度進行插補|
|[CCustomInterpolator::SetDuration](#setduration)|設定 interpolator 的持續時間。|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Interpolator 的起始值和速度設定。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|插補的值。|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|內插補點的速度。|
|[CCustomInterpolator::m_duration](#m_duration)|轉換的持續時間。|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|在轉換結束變數最終的值。|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|在轉換開始變數的值。|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|在轉換開始變數的速度。|

## <a name="remarks"></a>備註

CCustomInterpolator 從衍生類別並覆寫所有必要的方法，以便實作自訂內插補點演算法。 這個類別的指標應該做為參數傳遞至 CCustomTransition。

## <a name="inheritance-hierarchy"></a>繼承階層

`CCustomInterpolator`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="ccustominterpolator"></a>  CCustomInterpolator::CCustomInterpolator

建構自訂 interpolator 物件，並設定所有預設值為 0 的值。

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>參數

*持續時間*<br/>
轉換的持續時間。

*finalValue*

### <a name="remarks"></a>備註

您可以使用 CCustomInterpolator::Init 初始化期間以及最終的值，稍後在程式碼。

##  <a name="getdependencies"></a>  CCustomInterpolator::GetDependencies

取得 interpolator 的相依性。

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>參數

*initialValueDependencies*<br/>
輸出。 層面 interpolator 相依於的初始值會傳遞至 SetInitialValueAndVelocity。

*initialVelocityDependencies*<br/>
輸出。 Interpolator 的初始速度而定的各個層面會傳遞至 SetInitialValueAndVelocity。

*durationDependencies*<br/>
輸出。 Interpolator 的持續時間而定的層面會傳遞至 SetDuration。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

##  <a name="getduration"></a>  CCustomInterpolator::GetDuration

取得 interpolator 的持續時間。

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>參數

*持續時間*<br/>
輸出。 轉換，以秒為單位的持續時間。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

##  <a name="getfinalvalue"></a>  CCustomInterpolator::GetFinalValue

取得 interpolator 潛在客戶的最後一個值。

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>參數

*值*<br/>
輸出。 在轉換結束變數最終的值。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

##  <a name="init"></a>  CCustomInterpolator::Init

初始化期間以及最終的值。

```
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>參數

*持續時間*<br/>
轉換的持續時間。

*finalValue*<br/>
在轉換結束變數最終的值。

##  <a name="interpolatevalue"></a>  CCustomInterpolator::InterpolateValue

進行插補在指定的位移值。

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>參數

*值*<br/>
輸出。 插補的值。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

##  <a name="interpolatevelocity"></a>  CCustomInterpolator::InterpolateVelocity

指定位移處的速度進行插補

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>參數

*速度*<br/>
輸出。 在位移變數的速度。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

##  <a name="m_currentvalue"></a>  CCustomInterpolator::m_currentValue

插補的值。

```
DOUBLE m_currentValue;
```

##  <a name="m_currentvelocity"></a>  CCustomInterpolator::m_currentVelocity

內插補點的速度。

```
DOUBLE m_currentVelocity;
```

##  <a name="m_duration"></a>  CCustomInterpolator::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CCustomInterpolator::m_finalValue

在轉換結束變數最終的值。

```
DOUBLE m_finalValue;
```

##  <a name="m_initialvalue"></a>  CCustomInterpolator::m_initialValue

在轉換開始變數的值。

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomInterpolator::m_initialVelocity

在轉換開始變數的速度。

```
DOUBLE m_initialVelocity;
```

##  <a name="setduration"></a>  CCustomInterpolator::SetDuration

設定 interpolator 的持續時間。

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>參數

*持續時間*<br/>
轉換的持續時間。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

##  <a name="setinitialvalueandvelocity"></a>  CCustomInterpolator::SetInitialValueAndVelocity

Interpolator 的起始值和速度設定。

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>參數

*initialValue*<br/>
在轉換開始變數的值。

*initialVelocity*<br/>
在轉換開始變數的速度。

### <a name="return-value"></a>傳回值

基本的實作一定會傳回 TRUE。 傳回 FALSE 的覆寫實作如果您想要失敗事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
