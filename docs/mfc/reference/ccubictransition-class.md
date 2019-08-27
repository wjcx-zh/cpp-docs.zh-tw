---
title: CCubicTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: b6bb626f944ce87748809a5eb03a6f06f92c3de5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507133"
---
# <a name="ccubictransition-class"></a>CCubicTransition 類別

封裝立方轉換。

## <a name="syntax"></a>語法

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|會建立轉換物件, 並初始化其參數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCubicTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|轉換結束時的動畫變數值。|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|變數在轉換結束時的速度。|
|[CCubicTransition::m_duration](#m_duration)|轉換的持續時間。|

## <a name="remarks"></a>備註

在三次轉換期間, 動畫變數的值會在轉換期間從其初始值變更為指定的最終值, 並以指定的速度結束。 由於所有轉換都會自動清除, 因此建議您使用 operator new 加以配置。 封裝的 IUIAnimationTransition COM 物件是由 CAnimationController:: AnimateGroup 所建立, 直到它是 Null 為止。 在建立此 COM 物件之後變更成員變數不會有任何作用。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="ccubictransition"></a>CCubicTransition:: CCubicTransition

會建立轉換物件, 並初始化其參數。

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

*finalValue*<br/>
轉換結束時的動畫變數值。

*finalVelocity*<br/>
變數在轉換結束時的速度。

##  <a name="create"></a>CCubicTransition:: Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
[IUIAnimationTransitionLibrary 介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標, 它會定義標準轉換的程式庫。

### <a name="return-value"></a>傳回值

如果成功建立轉換, 則為 TRUE;否則為 FALSE。

##  <a name="m_dblfinalvalue"></a>CCubicTransition:: m_dblFinalValue

轉換結束時的動畫變數值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>CCubicTransition:: m_dblFinalVelocity

變數在轉換結束時的速度。

```
DOUBLE m_dblFinalVelocity;
```

##  <a name="m_duration"></a>CCubicTransition:: m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
