---
title: CParabolicTransitionFromAcceleration 類別
ms.date: 11/04/2016
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
ms.openlocfilehash: 0aa5831e2262602ee46bd69031e5927a86b978e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364094"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 類別

封裝拋物線加速轉換。

## <a name="syntax"></a>語法

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[從加速中轉換的環數::從加速轉換的環代謝](#cparabolictransitionfromacceleration)|建構拋物面加速過渡,並用指定的參數初始化它。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[從加速轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[從加速轉換::m_dblAcceleration](#m_dblacceleration)|轉換期間動畫變數的加速度。|
|[從加速轉換::m_dblFinalValue](#m_dblfinalvalue)|過渡結束時動畫變數的值。|
|[從加速轉換::m_dblFinalVelocity](#m_dblfinalvelocity)|轉換結束時動畫變數的速度。|

## <a name="remarks"></a>備註

在拋物面加速過渡期間,動畫變數的值從初始值更改為以指定速度結束的最終值。 您可以通過指定加速度來控制變數到達最終值的速度。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[從加速過渡](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a>從加速中轉換的環數::從加速轉換的環代謝

建構拋物面加速過渡,並用指定的參數初始化它。

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>參數

*dbl 最終值*<br/>
過渡結束時動畫變數的值。

*dblFinal速度*<br/>
轉換結束時動畫變數的速度。

*dbl加速*<br/>
轉換期間動畫變數的加速度。

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a>從加速轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向過渡庫的指標,它負責創建標準轉換。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a>從加速轉換::m_dblAcceleration

轉換期間動畫變數的加速度。

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>從加速轉換::m_dblFinalValue

過渡結束時動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>從加速轉換::m_dblFinalVelocity

轉換結束時動畫變數的速度。

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
