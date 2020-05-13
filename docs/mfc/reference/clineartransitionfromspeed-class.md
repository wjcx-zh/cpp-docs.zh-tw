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
ms.openlocfilehash: 31c04c303e7e253ec4de41bf076130d19232aac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372260"
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
|[從速度轉換的C線性:從速度轉換的C線性轉換](#clineartransitionfromspeed)|建構線性速度過渡物件,並初始化其速度和最終值。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 線性轉換從速度:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C線性轉換速度::m_dblFinalValue](#m_dblfinalvalue)|過渡結束時動畫變數的值。|
|[C線性轉換速度::m_dblSpeed](#m_dblspeed)|變數速度的絕對值。|

## <a name="remarks"></a>備註

在線性速度轉換期間,動畫變數的值會以指定速率更改。 轉換的持續時間由初始值和指定最終值之間的差異決定。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[C 線性從速度轉換](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>從速度轉換的C線性:從速度轉換的C線性轉換

建構線性速度過渡物件,並初始化其速度和最終值。

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*dblSpeed*<br/>
變數速度的絕對值。

*dbl 最終值*<br/>
過渡結束時動畫變數的值。

## <a name="clineartransitionfromspeedcreate"></a><a name="create"></a>C 線性轉換從速度:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向[IUIAnimation 轉換庫介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標,該介面定義標準轉換庫。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="clineartransitionfromspeedm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>C線性轉換速度::m_dblFinalValue

過渡結束時動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionfromspeedm_dblspeed"></a><a name="m_dblspeed"></a>C線性轉換速度::m_dblSpeed

變數速度的絕對值。

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
