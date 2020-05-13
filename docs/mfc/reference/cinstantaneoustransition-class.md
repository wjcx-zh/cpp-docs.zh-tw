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
ms.openlocfilehash: 15c471d64309cc1358c9c5b0b33577261dd877f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372431"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition 類別

封裝瞬間的轉換。

## <a name="syntax"></a>語法

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[暫態轉換:C暫態轉換](#cinstantaneoustransition)|構造過渡物件並初始化其最終值。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[暫態轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[暫態轉換:m_dblFinalValue](#m_dblfinalvalue)|過渡結束時動畫變數的值。|

## <a name="remarks"></a>備註

在暫態轉換期間,動畫變數的值會立即從當前值更改為指定的最終值。 此轉換的持續時間始終為零。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[C 暫態轉換](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cinstantaneoustransitioncinstantaneoustransition"></a><a name="cinstantaneoustransition"></a>暫態轉換:C暫態轉換

構造過渡物件並初始化其最終值。

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>參數

*dbl 最終值*<br/>
過渡結束時動畫變數的值。

## <a name="cinstantaneoustransitioncreate"></a><a name="create"></a>暫態轉換:建立

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

## <a name="cinstantaneoustransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>暫態轉換:m_dblFinalValue

過渡結束時動畫變數的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
