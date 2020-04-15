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
ms.openlocfilehash: 2a32ee7921e927e25a5196d38c8f5ae350ab2b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375661"
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
|[離散轉換:C離散轉換](#cdiscretetransition)|構造離散過渡物件並初始化其參數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[離散轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[離散轉換::m_dblFinalValue](#m_dblfinalvalue)|過渡結束時動畫變數的值。|
|[離散轉換::m_delay](#m_delay)|將暫態開關延遲到最終值的時間量。|
|[離散轉換::m_hold](#m_hold)|將變數保留在其最終值的時間量。|

## <a name="remarks"></a>備註

在離散轉換期間,動畫變數在指定延遲時間保持初始值,然後即時切換到指定的最終值,並在給定的保持時間內保持該值。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[C 分離轉換](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cdiscretetransitioncdiscretetransition"></a><a name="cdiscretetransition"></a>離散轉換:C離散轉換

構造離散過渡物件並初始化其參數。

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>參數

*延遲*<br/>
將暫態開關延遲到最終值的時間量。

*dbl 最終值*<br/>
過渡結束時動畫變數的值。

*保持*<br/>
將變數保留在其最終值的時間量。

## <a name="cdiscretetransitioncreate"></a><a name="create"></a>離散轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*p庫*<br/>
指向[IUIAnimation 轉換庫介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標,該介面定義標準轉換庫。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="cdiscretetransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>離散轉換::m_dblFinalValue

過渡結束時動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="cdiscretetransitionm_delay"></a><a name="m_delay"></a>離散轉換::m_delay

將暫態開關延遲到最終值的時間量。

```
UI_ANIMATION_SECONDS m_delay;
```

## <a name="cdiscretetransitionm_hold"></a><a name="m_hold"></a>離散轉換::m_hold

將變數保留在其最終值的時間量。

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
