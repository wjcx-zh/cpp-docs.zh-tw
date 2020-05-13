---
title: CSmoothStopTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
ms.openlocfilehash: 0ba550b4a0b9443d0681e17195687fb94c207ace
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318199"
---
# <a name="csmoothstoptransition-class"></a>CSmoothStopTransition 類別

封裝平滑停止轉換。

## <a name="syntax"></a>語法

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C"平滑停止轉換"::C"平滑停止轉換"](#csmoothstoptransition)|構造平穩停止過渡並初始化其最大持續時間和最終值。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C平滑停止轉換::建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C「平滑停止轉換::m_dblFinalValue](#m_dblfinalvalue)|過渡結束時動畫變數的值。|
|[C「平滑停止轉換::m_maximumDuration](#m_maximumduration)|轉換的最大持續時間。|

## <a name="remarks"></a>備註

平穩停止過渡在接近給定的最終值時變慢,並且以零的速度到達它。 轉換的持續時間由初始速度、初始值和最終值之間的差異以及指定的最長持續時間決定。 如果沒有由單個拋物線弧組成的解,則此方法將創建立方過渡。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[C平滑停止轉換](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="csmoothstoptransitioncreate"></a><a name="create"></a>C平滑停止轉換::建立

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

## <a name="csmoothstoptransitioncsmoothstoptransition"></a><a name="csmoothstoptransition"></a>C"平滑停止轉換"::C"平滑停止轉換"

構造平穩停止過渡並初始化其最大持續時間和最終值。

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*最大持續時間*<br/>
轉換的最大持續時間。

*dbl 最終值*<br/>
過渡結束時動畫變數的值。

## <a name="csmoothstoptransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>C「平滑停止轉換::m_dblFinalValue

過渡結束時動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="csmoothstoptransitionm_maximumduration"></a><a name="m_maximumduration"></a>C「平滑停止轉換::m_maximumDuration

轉換的最大持續時間。

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
