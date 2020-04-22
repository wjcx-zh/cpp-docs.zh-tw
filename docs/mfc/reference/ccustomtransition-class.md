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
ms.openlocfilehash: 76e0d12308ad579e4bdf9866dfcf1cde231a2d0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749147"
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
|[C自訂轉換:C自訂轉換](#ccustomtransition)|建構自定義轉換物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C自訂轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|
|[C自訂轉換::設定初始值](#setinitialvalue)|設置初始值,該值將應用於與此轉換關聯的動畫變數。|
|[C自訂轉換::設定初始速度](#setinitialvelocity)|設置初始速度,它將應用於與此轉換關聯的動畫變數。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[C自訂轉換:m_bInitialValueSpecified](#m_binitialvaluespecified)|指定初始值是否使用 Set 初始值指定。|
|[C自定義轉換::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定初始速度是否使用 Set 初始速度指定。|
|[C自定義轉換::m_initialValue](#m_initialvalue)|存儲初始值。|
|[C自定義轉換::m_initialVelocity](#m_initialvelocity)|存儲初始速度。|
|[CCustom 轉換::m_pInterpolator](#m_pinterpolator)|存儲指向自定義插值器的指標。|

## <a name="remarks"></a>備註

CCustomTransitions 類允許開發人員實現自定義轉換。 它創建並用作標準轉換,但其構造函數接受作為參數指向自定義插值器的指標。 執行以下步驟以使用自定義轉換:1。 從 CCustomInterpolator 派生類,並實現至少插值值方法。 2. 確保自定義插值器物件的存留期必須長於使用該物件的動畫持續時間。 3. 實例化(使用運算符 new)CCustomTransition 物件,並將指標傳遞到建構函數中的自定義插值器。 4. 調用 CCustom 轉換::設定初始值和 CCustom 轉換::如果自定義插值需要這些參數,則設置初始速度。 5. 將指向自定義轉換的指標傳遞給動畫物件的 AddTransition 方法,其值應使用自定義演演演算法進行動畫處理。 6. 當動畫物件的值應更改 Windows 動畫 API 時,將在 CCustomInterpolator 中調用插值值(和其他相關方法)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>C自訂轉換:C自訂轉換

建構自定義轉換物件。

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>參數

*p插值器*<br/>
指向自定義插值器的指標。

## <a name="ccustomtransitioncreate"></a><a name="create"></a>C自訂轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>參數

*pFactory*<br/>
指向轉換工廠的指標,它負責創建自定義轉換。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

此方法還可以設置初始值和初始速度以應用於動畫變數,該變數與此轉換相關聯。 為此,您必須在框架創建封裝的過渡 COM 物件之前調用 Set初始值和 Set初始速度(當您調用 CAnimateController::AnimateGroup)時,將呼叫 SetValueValue 和 Set初始速度。

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>C自訂轉換:m_bInitialValueSpecified

指定初始值是否使用 Set 初始值指定。

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>C自定義轉換::m_bInitialVelocitySpecified

指定初始速度是否使用 Set 初始速度指定。

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>C自定義轉換::m_initialValue

存儲初始值。

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>C自定義轉換::m_initialVelocity

存儲初始速度。

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustom 轉換::m_pInterpolator

存儲指向自定義插值器的指標。

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>C自訂轉換::設定初始值

設置初始值,該值將應用於與此轉換關聯的動畫變數。

```cpp
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>參數

*初始值*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>C自訂轉換::設定初始速度

設置初始速度,它將應用於與此轉換關聯的動畫變數。

```cpp
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>參數

*初始速度*

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
