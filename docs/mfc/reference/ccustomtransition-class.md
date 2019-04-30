---
title: CCustomTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: e0e5250b27ce6b902939ebcbfa03bf022a202788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391279"
---
# <a name="ccustomtransition-class"></a>CCustomTransition 類別

實作自訂的轉換。

## <a name="syntax"></a>語法

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|建構自訂的轉換物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCustomTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|設定初始的值，將會套用到這項轉換相關聯的動畫變數。|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|設定將套用至這項轉換相關聯的動畫變數的初始速度。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|指定與 SetInitialValue 是否已指定的初始值。|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定與 SetInitialVelocity 是否已指定的初始速度。|
|[CCustomTransition::m_initialValue](#m_initialvalue)|儲存的初始值。|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|儲存的初始速度。|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|儲存自訂 interpolator 的指標。|

## <a name="remarks"></a>備註

CCustomTransitions 類別可讓開發人員實作自訂的轉換。 建立和做為標準的轉換，但其建構函式做為參數會接受自訂 interpolator 的指標。 執行下列步驟，以使用自訂的轉換：1. CCustomInterpolator 從衍生類別，並至少會實作 InterpolateValue 方法。 2. 請確定，自訂 interpolator 物件的存留期必須超過的動畫的持續時間使用的位置。 3. 具現化 （使用運算子 new） CCustomTransition 物件並將指標傳遞給建構函式中的自訂 interpolator。 4. 如果這些參數所需的自訂內插補點，請呼叫 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity。 5. 將指標傳遞自訂轉換動畫物件，其值應該使用自訂的演算法建立動畫的方法。 6. 當動畫之物件的值應該變更 Windows 動畫 API 會在 CCustomInterpolator 中呼叫 InterpolateValue （和其他相關的方法）。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

建構自訂的轉換物件。

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>參數

*pInterpolator*<br/>
自訂 interpolator 指標。

##  <a name="create"></a>  CCustomTransition::Create

呼叫轉換程式庫來建立封裝的轉換 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>參數

*pFactory*<br/>
轉換處理站，也就是負責建立的自訂轉換指標。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

這個方法也可以設定的初始值，要套用至動畫變數，也就是這項轉換相關聯的初始速度。 針對此目的，您必須呼叫 SetInitialValue 和 SetInitialVelocity 之前此架構會建立封裝的轉換 COM 物件 （它發生時呼叫 CAnimationController::AnimateGroup）。

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

指定與 SetInitialValue 是否已指定的初始值。

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

指定與 SetInitialVelocity 是否已指定的初始速度。

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

儲存的初始值。

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

儲存的初始速度。

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

儲存自訂 interpolator 的指標。

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

設定初始的值，將會套用到這項轉換相關聯的動畫變數。

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>參數

*initialValue*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

設定將套用至這項轉換相關聯的動畫變數的初始速度。

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>參數

*initialVelocity*

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
