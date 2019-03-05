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
ms.openlocfilehash: 1efa9806267958b4221ee112e56f242c7e25a8f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260695"
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
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|建構線性速度轉換物件，並使用速度和最終值將它初始化。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|變數的速度的絕對值。|

## <a name="remarks"></a>備註

在線性速度轉換動畫變數的值變更的指定速率。 轉換的持續時間取決於初始的值與指定的最終值之間的差異。 因為所有的轉換會自動清除，所以建議配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup 之前, 則是 NULL。 不會影響這個 COM 物件建立後，請變更成員變數。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>  CLinearTransitionFromSpeed::CLinearTransitionFromSpeed

建構線性速度轉換物件，並使用速度和最終值將它初始化。

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*dblSpeed*<br/>
變數的速度的絕對值。

*dblFinalValue*<br/>
結尾的轉換動畫變數的值。

##  <a name="create"></a>  CLinearTransitionFromSpeed::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
指標[IUIAnimationTransitionLibrary 介面](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)，其定義的標準轉換程式庫。

### <a name="return-value"></a>傳回值

如果轉換成功; 建立，則為 TRUE。否則為 FALSE。

##  <a name="m_dblfinalvalue"></a>  CLinearTransitionFromSpeed::m_dblFinalValue

結尾的轉換動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>  CLinearTransitionFromSpeed::m_dblSpeed

變數的速度的絕對值。

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
