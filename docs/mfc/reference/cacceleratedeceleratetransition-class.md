---
title: CAccelerateDecelerateTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371154"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition 類別

實作加速減速轉換。

## <a name="syntax"></a>語法

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C加速減速轉換::C加速減速轉換](#cacceleratedeceleratetransition)|構造過渡物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C加速減速轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C加速減速轉換::m_accelerationRatio](#m_accelerationratio)|加速時間與持續時間的比率。|
|[C加速減速轉換::m_decelerationRatio](#m_decelerationratio)|減速時間與持續時間的比率。|
|[C加速減速轉換::m_duration](#m_duration)|轉換的持續時間。|
|[C加速減速轉換::m_finalValue](#m_finalvalue)|過渡結束時動畫變數的值。|

## <a name="remarks"></a>備註

在加速減速轉換期間,動畫變數會加速,然後在轉換期間減慢速度,以指定值結束。 通過指定不同的加速和減速比,您可以控制變數獨立加速和減速的速度。 當初始速度為零時,加速度比是變數將加速花費的持續時間的一小部分;同樣與減速率。 如果初始速度是非零,則它是速度達到零和過渡結束之間的時間分數。 加速度比和減速率應總和為最大 1.0。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>C加速減速轉換::C加速減速轉換

構造過渡物件。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>參數

*時間*<br/>
轉換的持續時間。

*最終價值*<br/>
過渡結束時動畫變數的值。

*加速度比*<br/>
加速時間與持續時間的比率。

*減速比*<br/>
減速時間與持續時間的比率。

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>C加速減速轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向[IUIAnimation 轉換庫介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標,該介面定義標準轉換庫。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>C加速減速轉換::m_accelerationRatio

加速時間與持續時間的比率。

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>C加速減速轉換::m_decelerationRatio

減速時間與持續時間的比率。

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>C加速減速轉換::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>C加速減速轉換::m_finalValue

過渡結束時動畫變數的值。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
