---
title: CLinearTransitionFromSpeed 類別
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 50c958a092478f4b9ec4e94f9e5e973a74c334c2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505718"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed 類別

封裝線性速度轉換。

## <a name="syntax"></a>語法

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|會建立線性速度轉換物件, 並以速度和最終值進行初始化。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|轉換結束時的動畫變數值。|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|變數速度的絕對值。|

## <a name="remarks"></a>備註

線上性速度轉換期間, 動畫變數的值會以指定的速率變更。 轉換的持續時間取決於初始值與指定的最後值之間的差異。 由於所有轉換都會自動清除, 因此建議您使用 operator new 加以配置。 封裝的 IUIAnimationTransition COM 物件是由 CAnimationController:: AnimateGroup 所建立, 直到它是 Null 為止。 在建立此 COM 物件之後變更成員變數不會有任何作用。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed:: CLinearTransitionFromSpeed

會建立線性速度轉換物件, 並以速度和最終值進行初始化。

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*dblSpeed*<br/>
變數速度的絕對值。

*dblFinalValue*<br/>
轉換結束時的動畫變數值。

##  <a name="create"></a>CLinearTransitionFromSpeed:: Create

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

##  <a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed:: m_dblFinalValue

轉換結束時的動畫變數值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>CLinearTransitionFromSpeed:: m_dblSpeed

變數速度的絕對值。

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
