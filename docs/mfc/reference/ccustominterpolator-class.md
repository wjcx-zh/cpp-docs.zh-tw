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
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749169"
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
|[海關組織::海關插值器](#ccustominterpolator)|已多載。 建構自訂插值器物件,並將持續時間和速度初始化到指定值。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCustom 插值器::取得相依性](#getdependencies)|獲取插值器的依賴項。|
|[CCustom 插值器:取得持續時間](#getduration)|獲取插值器的持續時間。|
|[CCustom 插值器::取得最終值](#getfinalvalue)|獲取插值器引由的最終值。|
|[CCustom插值器::Init](#init)|初始化持續時間和最終值。|
|[海關組織::刑警價值](#interpolatevalue)|插值在給定偏移處的值。|
|[海關刑警::刑警組織](#interpolatevelocity)|在給定位移插入速度|
|[C自訂設定器::設定持續時間](#setduration)|設置插值器的持續時間。|
|[C自訂插值器::設定初始值和速度](#setinitialvalueandvelocity)|設置插值器的初始值和速度。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[海關組織::m_currentValue](#m_currentvalue)|插值值。|
|[C自定義插值器::m_currentVelocity](#m_currentvelocity)|插值速度。|
|[C自定義插值器::m_duration](#m_duration)|轉換的持續時間。|
|[C自定義插值器::m_finalValue](#m_finalvalue)|轉換結束時變數的最終值。|
|[C自定義插值器::m_initialValue](#m_initialvalue)|轉換開始時變數的值。|
|[海關:m_initialVelocity](#m_initialvelocity)|轉換開始時變數的速度。|

## <a name="remarks"></a>備註

從 CCustomInterpolator 派生一個類並重寫所有必要的方法,以實現自訂插值演演演算法。 指向此類的指標應作為參數傳遞給 CCustomTransition。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CCustomInterpolator`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>海關組織::海關插值器

建構自定義插值器物件,並將所有值設置為預設 0。

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

*最終價值*

### <a name="remarks"></a>備註

使用 CCustomInterpolator::Init 在代碼的後面部分初始化持續時間和最終值。

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustom 插值器::取得相依性

獲取插值器的依賴項。

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>參數

*初始價值相依性*<br/>
輸出。 插值器的一些方面,這些插值取決於傳遞給 Set初始值和Velocity 的初始值。

*初始速度相依性*<br/>
輸出。 插值器的方面,這些插值器取決於傳遞給 Set 初始值和Velocity的初始速度。

*持續時間 相依*<br/>
輸出。 插值器的一些方面,這些插值器取決於傳遞給 SetDuration 的持續時間。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustom 插值器:取得持續時間

獲取插值器的持續時間。

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>參數

*duration*<br/>
輸出。 轉換的持續時間,以秒為單位。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustom 插值器::取得最終值

獲取插值器引由的最終值。

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>參數

*value*<br/>
輸出。 轉換結束時變數的最終值。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustom插值器::Init

初始化持續時間和最終值。

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

*最終價值*<br/>
轉換結束時變數的最終值。

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>海關組織::刑警價值

插值在給定偏移處的值。

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>參數

*value*<br/>
輸出。 插值值。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>海關刑警::刑警組織

在給定位移插入速度

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>參數

*velocity*<br/>
輸出。 偏移處變數的速度。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>海關組織::m_currentValue

插值值。

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>C自定義插值器::m_currentVelocity

插值速度。

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>C自定義插值器::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>C自定義插值器::m_finalValue

轉換結束時變數的最終值。

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>C自定義插值器::m_initialValue

轉換開始時變數的值。

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>海關:m_initialVelocity

轉換開始時變數的速度。

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>C自訂設定器::設定持續時間

設置插值器的持續時間。

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>C自訂插值器::設定初始值和速度

設置插值器的初始值和速度。

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>參數

*初始值*<br/>
轉換開始時變數的值。

*初始速度*<br/>
轉換開始時變數的速度。

### <a name="return-value"></a>傳回值

基本實現始終返回 TRUE。 如果要使事件失敗,則從重寫的實現返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
