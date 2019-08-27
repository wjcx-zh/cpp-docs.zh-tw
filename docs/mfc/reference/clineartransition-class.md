---
title: CLinearTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
ms.openlocfilehash: 1a6348d1afd0117683bd31af61324b14e16f710c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505735"
---
# <a name="clineartransition-class"></a>CLinearTransition 類別

封裝線性轉換。

## <a name="syntax"></a>語法

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CLinearTransition:: CLinearTransition](#clineartransition)|會建立線性轉換物件, 並以持續時間和最終值進行初始化。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CLinearTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|轉換結束時的動畫變數值。|
|[CLinearTransition::m_duration](#m_duration)|轉換的持續時間。|

## <a name="remarks"></a>備註

線上性轉換期間, 動畫變數的值會從其初始值以線性方式轉換成指定的最終值。 由於所有轉換都會自動清除, 因此建議您使用 operator new 加以配置。 封裝的 IUIAnimationTransition COM 物件是由 CAnimationController:: AnimateGroup 所建立, 直到它是 Null 為止。 在建立此 COM 物件之後變更成員變數不會有任何作用。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransition](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="clineartransition"></a>CLinearTransition:: CLinearTransition

會建立線性轉換物件, 並以持續時間和最終值進行初始化。

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*duration*<br/>
轉換的持續時間。

*dblFinalValue*<br/>
轉換結束時的動畫變數值。

##  <a name="create"></a>CLinearTransition:: Create

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

##  <a name="m_dblfinalvalue"></a>CLinearTransition:: m_dblFinalValue

轉換結束時的動畫變數值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_duration"></a>CLinearTransition:: m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
