---
title: CDiscreteTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: 7087dfa13972737f0a1244d2cc9a7088b23dc184
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506859"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 類別

封裝離散的轉換。

## <a name="syntax"></a>語法

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|會建立離散的轉換物件, 並初始化其參數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDiscreteTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|轉換結束時的動畫變數值。|
|[CDiscreteTransition::m_delay](#m_delay)|要延遲瞬間切換為最終值的時間量。|
|[CDiscreteTransition::m_hold](#m_hold)|將變數保留在其最終值的時間量。|

## <a name="remarks"></a>備註

在離散轉換期間, 動畫變數會保留在指定之延遲時間的初始值, 然後立即切換為指定的最後值, 並在指定的保存時間保留該值。 由於所有轉換都會自動清除, 因此建議您使用 operator new 加以配置。 封裝的 IUIAnimationTransition COM 物件是由 CAnimationController:: AnimateGroup 所建立, 直到它是 Null 為止。 在建立此 COM 物件之後變更成員變數不會有任何作用。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cdiscretetransition"></a>CDiscreteTransition:: CDiscreteTransition

會建立離散的轉換物件, 並初始化其參數。

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>參數

*delay*<br/>
要延遲瞬間切換為最終值的時間量。

*dblFinalValue*<br/>
轉換結束時的動畫變數值。

*握*<br/>
將變數保留在其最終值的時間量。

##  <a name="create"></a>CDiscreteTransition:: Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
[IUIAnimationTransitionLibrary 介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標, 它會定義標準轉換的程式庫。

### <a name="return-value"></a>傳回值

如果成功建立轉換, 則為 TRUE;否則為 FALSE。

##  <a name="m_dblfinalvalue"></a>CDiscreteTransition:: m_dblFinalValue

轉換結束時的動畫變數值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>CDiscreteTransition:: m_delay

要延遲瞬間切換為最終值的時間量。

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>CDiscreteTransition:: m_hold

將變數保留在其最終值的時間量。

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
