---
title: CKeyFrame 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
dev_langs:
- C++
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5bdba80f0be5e6e47043b67934a79ea5039b4ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394235"
---
# <a name="ckeyframe-class"></a>CKeyFrame 類別

表示動畫主要畫面格。

## <a name="syntax"></a>語法

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|多載。 建構取決於其他主要畫面格的主要畫面格。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|將分鏡腳本中的主要畫面格。 (覆寫[CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|加入分鏡腳本轉換後的主要畫面格。|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|加入主要畫面格位移分鏡腳本。|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|讓指標回到這個主要畫面格取決於主要畫面格。|
|[CKeyFrame::GetOffset](#getoffset)|從其他主要畫面格，會傳回位移。|
|[CKeyFrame::GetTransition](#gettransition)|傳回的轉換，取決於這個主要畫面格指標。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|指定這個主要畫面格，從儲存在 m_pExistingKeyFrame 主要畫面格位移。|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|儲存現有的 keframe 的指標。 這個主要畫面格會新增至現有的主要畫面格 m_offset 使用分鏡腳本。|
|[CKeyFrame::m_pTransition](#m_ptransition)|儲存的指標，以開始這個主要畫面格的轉換。|

## <a name="remarks"></a>備註

這個類別會實作動畫主要畫面格。 主要畫面格代表時間的分鏡腳本內的時間點，而且可用來指定開始和結束時間的轉換。 主要畫面格可能會根據其他主要畫面格位移 （以秒為單位），或可能會根據轉換，以及擁有代表這項轉換的結束的時間的某個時間點。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard

將分鏡腳本中的主要畫面格。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*pStoryboard*<br/>
分鏡腳本指標。

*bDeepAdd*<br/>
指定是否要加入主要畫面格，或轉換以遞迴方式。

### <a name="return-value"></a>傳回值

如果為 TRUE，已成功新增主要畫面格。

### <a name="remarks"></a>備註

這個方法將分鏡腳本主要畫面格。 如果它相依於其他主要畫面格或轉換 bDeepAdd 為 TRUE，這個方法會嘗試以遞迴方式加入它們。

##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition

加入分鏡腳本轉換後的主要畫面格。

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*pStoryboard*<br/>
分鏡腳本指標。

*bDeepAdd*<br/>
指定是否要轉換以遞迴方式加入。

### <a name="return-value"></a>傳回值

如果為 TRUE，已成功新增主要畫面格。

### <a name="remarks"></a>備註

要加入主要畫面格在轉換後的分鏡腳本的 framework 會呼叫此函式。

##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset

加入主要畫面格位移分鏡腳本。

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*pStoryboard*<br/>
分鏡腳本指標。

*bDeepAdd*<br/>
指定要加入主要畫面格這個主要畫面格是否相依於以遞迴方式。

### <a name="return-value"></a>傳回值

如果為 TRUE，已成功新增主要畫面格。

### <a name="remarks"></a>備註

要加入主要畫面格位移分鏡腳本的 framework 會呼叫此函式。

##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame

建構取決於轉換的主要畫面格。

```
CKeyFrame(CBaseTransition* pTransition);


CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>參數

*pTransition*<br/>
轉換指標。

*pKeyframe*<br/>
主要畫面格指標。

*offset*<br/>
以秒為單位，從主要畫面格 pkeyframe 指定的位移。

### <a name="remarks"></a>備註

指定的轉換結束時，建構的主要畫面格會呈現時間是在分鏡腳本某個時間點。

##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe

讓指標回到這個主要畫面格取決於主要畫面格。

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>傳回值

主要畫面格，則為 NULL。 如果這個主要畫面格不相依於其他主要畫面格有效指標。

### <a name="remarks"></a>備註

這是取決於這個主要畫面格的主要畫面格的存取子。

##  <a name="getoffset"></a>  CKeyFrame::GetOffset

從其他主要畫面格，會傳回位移。

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>傳回值

位移 （秒），從其他主要畫面格。

### <a name="remarks"></a>備註

若要判斷位移 （秒），從其他主要畫面格，應該呼叫這個方法。

##  <a name="gettransition"></a>  CKeyFrame::GetTransition

傳回的轉換，取決於這個主要畫面格指標。

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>傳回值

轉換或如果這個主要畫面格不需依賴轉換為 NULL 的有效指標。

### <a name="remarks"></a>備註

這是的轉換，取決於這個主要畫面格的存取子。

##  <a name="m_offset"></a>  CKeyFrame::m_offset

指定這個主要畫面格，從儲存在 m_pExistingKeyFrame 主要畫面格位移。

```
UI_ANIMATION_SECONDS m_offset;
```

##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame

儲存現有的 keframe 的指標。 這個主要畫面格會新增至現有的主要畫面格 m_offset 使用分鏡腳本。

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition

儲存的指標，以開始這個主要畫面格的轉換。

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
