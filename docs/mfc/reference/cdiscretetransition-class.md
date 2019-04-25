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
ms.openlocfilehash: dc2311f7dae71f7c3848b7825b297ec5c9747859
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168007"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 類別

封裝離散的轉換。

## <a name="syntax"></a>語法

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|建構一個離散轉換物件並初始化其參數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDiscreteTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|
|[CDiscreteTransition::m_delay](#m_delay)|用來延遲的最終值即時切換的時間量。|
|[CDiscreteTransition::m_hold](#m_hold)|用來保存的變數，在最後一個值的時間量。|

## <a name="remarks"></a>備註

離散的轉換，期間動畫變數會保持在初始的值指定的延遲時間，然後立即交換器指定的最後一個值，以及維持該值指定的保留時間。 因為所有的轉換會自動清除，所以建議配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup 之前, 則是 NULL。 不會影響這個 COM 物件建立後，請變更成員變數。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cdiscretetransition"></a>  CDiscreteTransition::CDiscreteTransition

建構一個離散轉換物件並初始化其參數。

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>參數

*delay*<br/>
用來延遲的最終值即時切換的時間量。

*dblFinalValue*<br/>
結尾的轉換動畫變數的值。

*hold*<br/>
用來保存的變數，在最後一個值的時間量。

##  <a name="create"></a>  CDiscreteTransition::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
指標[IUIAnimationTransitionLibrary 介面](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)，其定義的標準轉換程式庫。

### <a name="return-value"></a>傳回值

如果轉換成功; 建立，則為 TRUE。否則為 FALSE。

##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue

結尾的轉換動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>  CDiscreteTransition::m_delay

用來延遲的最終值即時切換的時間量。

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>  CDiscreteTransition::m_hold

用來保存的變數，在最後一個值的時間量。

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
