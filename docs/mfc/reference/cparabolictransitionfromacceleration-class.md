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
ms.openlocfilehash: 3d4a073a0fd74f7564d9183779acfd66b41a9540
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274410"
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
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|建構的拋物線加速轉換，並使用指定的參數將它初始化。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|在轉換期間加速動畫變數。|
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|結尾的轉換動畫變數的速度。|

## <a name="remarks"></a>備註

拋物線加速轉換期間動畫變數的值變更的起始值的結束時間指定速度的最終值。 您可以控制變數達到最終的值指定加速射的速度。 因為所有的轉換會自動清除，所以建議配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup 之前, 則是 NULL。 不會影響這個 COM 物件建立後，請變更成員變數。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cparabolictransitionfromacceleration"></a>  CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration

建構的拋物線加速轉換，並使用指定的參數將它初始化。

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>參數

*dblFinalValue*<br/>
結尾的轉換動畫變數的值。

*dblFinalVelocity*<br/>
結尾的轉換動畫變數的速度。

*dblAcceleration*<br/>
在轉換期間加速動畫變數。

##  <a name="create"></a>  CParabolicTransitionFromAcceleration::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
轉換程式庫，也就是負責建立的標準轉換指標。

### <a name="return-value"></a>傳回值

如果轉換成功; 建立，則為 TRUE。否則為 FALSE。

##  <a name="m_dblacceleration"></a>  CParabolicTransitionFromAcceleration::m_dblAcceleration

在轉換期間加速動畫變數。

```
DOUBLE m_dblAcceleration;
```

##  <a name="m_dblfinalvalue"></a>  CParabolicTransitionFromAcceleration::m_dblFinalValue

結尾的轉換動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>  CParabolicTransitionFromAcceleration::m_dblFinalVelocity

結尾的轉換動畫變數的速度。

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
