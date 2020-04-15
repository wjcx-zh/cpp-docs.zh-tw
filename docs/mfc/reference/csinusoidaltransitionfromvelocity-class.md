---
title: CSinusoidalTransitionFromVelocity 類別
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_period
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity [MFC], CSinusoidalTransitionFromVelocity
- CSinusoidalTransitionFromVelocity [MFC], Create
- CSinusoidalTransitionFromVelocity [MFC], m_duration
- CSinusoidalTransitionFromVelocity [MFC], m_period
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
ms.openlocfilehash: 0df9ca6d140cb9e3ec85be3ce32760a66599c5d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318238"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>CSinusoidalTransitionFromVelocity 類別

封裝由動畫變數的初始速度決定其幅度的正弦曲線速度轉換。

## <a name="syntax"></a>語法

```
class CSinusoidalTransitionFromVelocity : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[從速度的CSinusoid過渡:從速度中轉換的CSinusoid](#csinusoidaltransitionfromvelocity)|構造過渡物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[從速度轉換的 CSinusoid 轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[從速度轉換的CSinusoid轉換::m_duration](#m_duration)|轉換的持續時間。|
|[從速度轉換的CSinusoid轉換::m_period](#m_period)|正弦波的振蕩週期(以秒為單位)。|

## <a name="remarks"></a>備註

動畫變數的值在正弦範圍轉換的整個持續時間內圍繞初始值振蕩。 振蕩的振幅由轉換開始時動畫變數的速度決定。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[從速度轉換的 CSinusoid](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromvelocitycreate"></a><a name="create"></a>從速度轉換的 CSinusoid 轉換:建立

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

## <a name="csinusoidaltransitionfromvelocitycsinusoidaltransitionfromvelocity"></a><a name="csinusoidaltransitionfromvelocity"></a>從速度的CSinusoid過渡:從速度中轉換的CSinusoid

構造過渡物件。

```
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,
    UI_ANIMATION_SECONDS period);
```

### <a name="parameters"></a>參數

*時間*<br/>
轉換的持續時間。

*時期*<br/>
正弦波的振蕩週期(以秒為單位)。

## <a name="csinusoidaltransitionfromvelocitym_duration"></a><a name="m_duration"></a>從速度轉換的CSinusoid轉換::m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromvelocitym_period"></a><a name="m_period"></a>從速度轉換的CSinusoid轉換::m_period

正弦波的振蕩週期(以秒為單位)。

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
