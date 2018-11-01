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
ms.openlocfilehash: 41ff87f82b695ba07723c1dac8cd2d5148f6f162
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578421"
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
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|建構平滑停止轉換，並初始化其最大持續期限和最終值。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSmoothStopTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|轉換的最大持續時間。|

## <a name="remarks"></a>備註

平滑停止轉換會減慢接近特定的最後一個值，並達到與速度為零。 轉換的持續時間取決於初始速度，也就是初始和最終值，與指定的最大持續期限之間的差異。 如果沒有單一的拋物線弧線所組成的解決方案，此方法會建立三次方的轉換。 因為所有的轉換會自動清除，所以建議配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup 之前, 則是 NULL。 不會影響這個 COM 物件建立後，請變更成員變數。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="create"></a>  CSmoothStopTransition::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
轉換程式庫，也就是負責建立的標準轉換指標。

### <a name="return-value"></a>傳回值

如果轉換成功; 建立，則為 TRUE。否則為 FALSE。

##  <a name="csmoothstoptransition"></a>  CSmoothStopTransition::CSmoothStopTransition

建構平滑停止轉換，並初始化其最大持續期限和最終值。

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*maximumDuration*<br/>
轉換的最大持續時間。

*dblFinalValue*<br/>
結尾的轉換動畫變數的值。

##  <a name="m_dblfinalvalue"></a>  CSmoothStopTransition::m_dblFinalValue

結尾的轉換動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_maximumduration"></a>  CSmoothStopTransition::m_maximumDuration

轉換的最大持續時間。

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
