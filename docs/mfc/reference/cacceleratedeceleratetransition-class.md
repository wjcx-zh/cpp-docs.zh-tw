---
title: CAccelerateDecelerateTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 1e55e81b4d9b5c324f86bfd141b74d9faa362d94
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507747"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition 類別

實作加速減速轉換。

## <a name="syntax"></a>語法

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|構造轉換物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|花費在加速到持續時間的時間比例。|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|花費在減速期間的時間比例。|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|轉換的持續時間。|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|轉換結束時的動畫變數值。|

## <a name="remarks"></a>備註

在加速減速轉換期間, 動畫變數會加速, 然後在轉換期間 (以指定的值結束) 進行減速。 您可以藉由指定不同的加速和減速比例, 分別控制變數加速和減速的速度。 當初始速度為零時, 加速比率是變數將花費在加速的持續時間的分數;同樣地, 與減速比率相同。 如果初始速度不是零, 則是速度達到零和轉換結束之間的時間分數。 加速比率和減速比率應加上最大值1.0。 由於所有轉換都會自動清除, 因此建議您使用 operator new 加以配置。 封裝的 IUIAnimationTransition COM 物件是由 CAnimationController:: AnimateGroup 所建立, 直到它是 Null 為止。 在建立此 COM 物件之後變更成員變數不會有任何作用。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

構造轉換物件。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

*finalValue*<br/>
轉換結束時的動畫變數值。

*accelerationRatio*<br/>
花費在加速到持續時間的時間比例。

*decelerationRatio*<br/>
花費在減速期間的時間比例。

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
[IUIAnimationTransitionLibrary 介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標, 它會定義標準轉換的程式庫。

### <a name="return-value"></a>傳回值

如果成功建立轉換, 則為 TRUE;否則為 FALSE。

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

花費在加速到持續時間的時間比例。

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

花費在減速期間的時間比例。

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

轉換結束時的動畫變數值。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
