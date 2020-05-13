---
title: CSinusoidalTransitionFromRange 類別
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
ms.openlocfilehash: 0612a4b365b928d3c9be6d76168a76b4ee1caa85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318262"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange 類別

封裝已指定振動範圍的正弦曲線範圍轉換。

## <a name="syntax"></a>語法

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[從範圍轉換的CSinusoid轉換:從範圍轉換的CSinusoid](#csinusoidaltransitionfromrange)|構造過渡物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSinusoid 從範圍轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSinusoid 從範圍轉換::m_dblMaximumValue](#m_dblmaximumvalue)|正弦波峰值處動畫變數的值。|
|[CSinusoid 從範圍轉換::m_dblMinimumValue](#m_dblminimumvalue)|正弦波槽處動畫變數的值。|
|[CSinusoid 從範圍轉換::m_duration](#m_duration)|轉換的持續時間。|
|[CSinusoid 從範圍轉換::m_period](#m_period)|正弦波的振蕩週期(以秒為單位)。|
|[CSinusoid 從範圍轉換::m_slope](#m_slope)|過渡開始時的斜率。|

## <a name="remarks"></a>備註

動畫變數的值在正弦範圍轉換的整個持續時間內在指定的最小值和最大值之間波動。 坡度參數用於消除其他參數指定的兩個可能的正子波之間的歧義。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[從範圍轉換的 CSinusoid](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromrangecreate"></a><a name="create"></a>CSinusoid 從範圍轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向過渡庫的指標,它負責創建標準轉換。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="csinusoidaltransitionfromrangecsinusoidaltransitionfromrange"></a><a name="csinusoidaltransitionfromrange"></a>從範圍轉換的CSinusoid轉換:從範圍轉換的CSinusoid

構造過渡物件。

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>參數

*時間*<br/>
轉換的持續時間。

*最小值*<br/>
正弦波槽處動畫變數的值。

*最大值*<br/>
正弦波峰值處動畫變數的值。

*時期*<br/>
正弦波的振蕩週期(以秒為單位)。

*slope*<br/>
過渡開始時的斜率。

## <a name="csinusoidaltransitionfromrangem_dblmaximumvalue"></a><a name="m_dblmaximumvalue"></a>CSinusoid 從範圍轉換::m_dblMaximumValue

正弦波峰值處動畫變數的值。

```
DOUBLE m_dblMaximumValue;
```

## <a name="csinusoidaltransitionfromrangem_dblminimumvalue"></a><a name="m_dblminimumvalue"></a>CSinusoid 從範圍轉換::m_dblMinimumValue

正弦波槽處動畫變數的值。

```
DOUBLE m_dblMinimumValue;
```

## <a name="csinusoidaltransitionfromrangem_duration"></a><a name="m_duration"></a>CSinusoid 從範圍轉換::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromrangem_period"></a><a name="m_period"></a>CSinusoid 從範圍轉換::m_period

正弦波的振蕩週期(以秒為單位)。

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="csinusoidaltransitionfromrangem_slope"></a><a name="m_slope"></a>CSinusoid 從範圍轉換::m_slope

過渡開始時的斜率。

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
