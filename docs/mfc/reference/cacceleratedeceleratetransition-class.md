---
title: Cacceleratedeceleratetransition 類別類別
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: f37670d6e965cb034b81a6fb9ec8cc252bd5ee31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614691"
---
# <a name="cacceleratedeceleratetransition-class"></a>Cacceleratedeceleratetransition 類別類別

實作加速減速轉換。

## <a name="syntax"></a>語法

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|建構轉換物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|加速的持續期間所花費的時間比例。|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|要減速的持續期間所花費的時間比例。|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|轉換的持續時間。|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|結尾的轉換動畫變數的值。|

## <a name="remarks"></a>備註

「 增進洞悉期間的減速轉換，並接著速度會變慢的轉換，結束指定的值時間的持續期間內加速動畫變數。 您可以控制變數可加速和減速獨立，藉由指定不同的加速與減速比例的速度。 初始速度為零，加速比率時，變數會花加速; 持續時間的比例同樣地與減速比率。 如果是非零值的初始速度，就到達零且轉換結束的速度之間的時間部份。 加速比例以及減速比率應該為 1.0 的最大值的總和。 因為所有的轉換會自動清除，所以建議配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup 之前, 則是 NULL。 不會影響這個 COM 物件建立後，請變更成員變數。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

建構轉換物件。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>參數

*持續時間*<br/>
轉換的持續時間。

*finalValue*<br/>
結尾的轉換動畫變數的值。

*accelerationRatio*<br/>
加速的持續期間所花費的時間比例。

*decelerationRatio*<br/>
要減速的持續期間所花費的時間比例。

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
指標[IUIAnimationTransitionLibrary 介面](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)，其定義的標準轉換程式庫。

### <a name="return-value"></a>傳回值

如果轉換成功; 建立，則為 TRUE。否則為 FALSE。

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

加速的持續期間所花費的時間比例。

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

要減速的持續期間所花費的時間比例。

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue

結尾的轉換動畫變數的值。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
