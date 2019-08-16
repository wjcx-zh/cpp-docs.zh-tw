---
title: CInstantaneousTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: f3861bbbc0fc138dcb0f2a8b969ed9bde41335bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505941"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition 類別

封裝瞬間的轉換。

## <a name="syntax"></a>語法

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|會建立轉換物件, 並初始化它的最終值。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CInstantaneousTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|轉換結束時的動畫變數值。|

## <a name="remarks"></a>備註

在瞬間轉換期間, 動畫變數的值會立即從目前的值變更為指定的最終值。 此轉換的持續時間一律為零。 由於所有轉換都會自動清除, 因此建議您使用 operator new 加以配置。 封裝的 IUIAnimationTransition COM 物件是由 CAnimationController:: AnimateGroup 所建立, 直到它是 Null 為止。 在建立此 COM 物件之後變更成員變數不會有任何作用。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="cinstantaneoustransition"></a>CInstantaneousTransition:: CInstantaneousTransition

會建立轉換物件, 並初始化它的最終值。

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*dblFinalValue*<br/>
轉換結束時的動畫變數值。

##  <a name="create"></a>CInstantaneousTransition:: Create

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

##  <a name="m_dblfinalvalue"></a>CInstantaneousTransition:: m_dblFinalValue

轉換結束時的動畫變數值。

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
