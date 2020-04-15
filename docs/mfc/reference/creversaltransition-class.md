---
title: CReversalTransition 類別
ms.date: 11/04/2016
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
ms.openlocfilehash: 73d12fb6bbaefcfac1437248ebe11f3a5c24c45b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368308"
---
# <a name="creversaltransition-class"></a>CReversalTransition 類別

封裝反轉的轉換。

## <a name="syntax"></a>語法

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 反轉轉換:c 反轉轉換](#creversaltransition)|構造反轉過渡物件並初始化其持續時間。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 反向轉換:建立](#create)|呼叫過渡庫以建立封裝的過渡 COM 物件。 ( 覆寫[CBase 轉換:建立](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C反向轉換:m_duration](#m_duration)|轉換的持續時間。|

## <a name="remarks"></a>備註

反轉過渡在給定持續時間內平滑地更改方向。 最終值將與初始值相同,最終速度為初始速度的負數。 由於所有轉換都將自動清除,因此建議使用運算符 new 分配。 封裝的 IUI動畫轉換 COM 物件由 C動畫控制器::AnimateGroup 創建,直到此為止,它才為 NULL。 建立此 COM 物件後更改成員變數不起作用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBase 轉換](../../mfc/reference/cbasetransition-class.md)

[C 反向轉換](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a>C 反向轉換:建立

呼叫過渡庫以建立封裝的過渡 COM 物件。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向過渡庫的指標,它負責創建標準轉換。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;如果成功創建轉換,則為 TRUE。否則 FALSE。

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a>C 反轉轉換:c 反轉轉換

構造反轉過渡物件並初始化其持續時間。

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>參數

*時間*<br/>
轉換的持續時間。

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a>C反向轉換:m_duration

轉換的持續時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
