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
ms.openlocfilehash: de376503111dab157ca34744863fb1d35a58785e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369339"
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
|[立方轉換:C立方轉換](#ccubictransition)|構造過渡物件並初始化其參數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCubic 轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCubic 轉換:m_dblFinalValue](#m_dblfinalvalue)|過渡結束時動畫變數的值。|
|[CCubic 轉換:m_dblFinalVelocity](#m_dblfinalvelocity)|轉換結束時變數的速度。|
|[CCubic 轉換:m_duration](#m_duration)|轉換的持續時間。|

## <a name="remarks"></a>備註

在立方過渡期間,動畫變數的值在過渡期間從初始值更改為指定的最終值,以指定速度結束。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="ccubictransitionccubictransition"></a><a name="ccubictransition"></a>立方轉換:C立方轉換

構造過渡物件並初始化其參數。

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>參數

*時間*<br/>
轉換的持續時間。

*最終價值*<br/>
過渡結束時動畫變數的值。

*最終速度*<br/>
轉換結束時變數的速度。

## <a name="ccubictransitioncreate"></a><a name="create"></a>CCubic 轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向[IUIAnimation 轉換庫介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標,該介面定義標準轉換庫。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="ccubictransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubic 轉換:m_dblFinalValue

過渡結束時動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="ccubictransitionm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubic 轉換:m_dblFinalVelocity

轉換結束時變數的速度。

```
DOUBLE m_dblFinalVelocity;
```

## <a name="ccubictransitionm_duration"></a><a name="m_duration"></a>CCubic 轉換:m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
