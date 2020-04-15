---
title: CKeyFrame 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372298"
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
|[鑰匙框架::CKeyFrame](#ckeyframe)|已多載。 構造依賴於其他關鍵幀的關鍵幀。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CKeyFrame::新增到故事板](#addtostoryboard)|向情節提要添加關鍵幀。 ( 覆[寫 CBaseKeyFrame: :新增到情節板](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。|
|[CKeyFrame:在過渡後新增到故事板](#addtostoryboardaftertransition)|過渡後向情節提要添加關鍵幀。|
|[CKeyframe::添加到故事板的偏移](#addtostoryboardatoffset)|在偏移時將關鍵幀添加到情節提要。|
|[關鍵幀:獲取現有關鍵幀](#getexistingkeyframe)|返回指向此關鍵幀所依賴的關鍵幀的指標。|
|[關鍵幀:取得偏移](#getoffset)|返回與其他關鍵幀的偏移量。|
|[關鍵幀:取得過渡](#gettransition)|返回指向此關鍵幀所依賴的過渡的指標。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[關鍵幀:m_offset](#m_offset)|指定此關鍵幀與存儲在m_pExistingKeyFrame的關鍵幀的偏移量。|
|[CKeyFrame:m_pExistingKeyFrame](#m_pexistingkeyframe)|存儲指向現有 keframe 的指標。 此關鍵幀將添加到情節提要中,m_offset添加到現有關鍵幀中。|
|[CKeyFrame:m_pTransition](#m_ptransition)|存儲從此關鍵幀開始的換轉指標。|

## <a name="remarks"></a>備註

此類實現動畫關鍵幀。 關鍵幀表示情節提要中的一個時刻,可用於指定過渡的開始和結束時間。 關鍵幀可能基於其他關鍵幀,並且具有偏移量(以秒為單位),或者可能基於過渡,並代表此轉換結束時的一個時刻。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKey 框架](../../mfc/reference/cbasekeyframe-class.md)

[基卡框架](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::新增到故事板

向情節提要添加關鍵幀。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標。

*bDeepAdd*<br/>
指定是遞歸添加關鍵幀還是轉換。

### <a name="return-value"></a>傳回值

如果成功添加了關鍵幀,則為 TRUE。

### <a name="remarks"></a>備註

此方法將關鍵幀添加到情節提要。 如果它依賴於其他關鍵幀或轉換,並且 bDeepAdd 為 TRUE,則此方法會嘗試遞歸添加它們。

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame:在過渡後新增到故事板

過渡後向情節提要添加關鍵幀。

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標。

*bDeepAdd*<br/>
指定是否遞歸添加轉換。

### <a name="return-value"></a>傳回值

如果成功添加了關鍵幀,則為 TRUE。

### <a name="remarks"></a>備註

框架調用此函數,以便在轉換后將關鍵幀添加到情節提要。

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyframe::添加到故事板的偏移

在偏移時將關鍵幀添加到情節提要。

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標。

*bDeepAdd*<br/>
指定是否添加此關鍵幀取決於遞歸的關鍵幀。

### <a name="return-value"></a>傳回值

如果成功添加了關鍵幀,則為 TRUE。

### <a name="remarks"></a>備註

框架調用此功能,以偏移時將關鍵幀添加到情節提要。

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>鑰匙框架::CKeyFrame

構造依賴於轉換的關鍵幀。

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>參數

*p 轉換*<br/>
指向轉換的指標。

*p 鍵框*<br/>
指向關鍵幀的指標。

*位移*<br/>
與 pKeyframe 指定的關鍵幀的偏移(以秒為單位)。

### <a name="remarks"></a>備註

構造的關鍵幀將在指定的過渡結束時在情節提要中表示一個時刻。

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>關鍵幀:獲取現有關鍵幀

返回指向此關鍵幀所依賴的關鍵幀的指標。

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>傳回值

如果此關鍵幀不依賴於其他關鍵幀,則指向關鍵幀的有效指標或 NULL。

### <a name="remarks"></a>備註

這是此關鍵幀所依賴的關鍵幀的訪問器。

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>關鍵幀:取得偏移

返回與其他關鍵幀的偏移量。

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>傳回值

與其他關鍵幀的偏移量(以秒為單位)。

### <a name="remarks"></a>備註

應調用此方法以確定與其他關鍵幀的偏移量(以秒為單位)。

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>關鍵幀:取得過渡

返回指向此關鍵幀所依賴的過渡的指標。

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>傳回值

如果此關鍵幀不依賴於轉換,則指向轉換的有效指標或NULL。

### <a name="remarks"></a>備註

這是此關鍵幀所依賴的過渡的訪問器。

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>關鍵幀:m_offset

指定此關鍵幀與存儲在m_pExistingKeyFrame的關鍵幀的偏移量。

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame:m_pExistingKeyFrame

存儲指向現有 keframe 的指標。 此關鍵幀將添加到情節提要中,m_offset添加到現有關鍵幀中。

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame:m_pTransition

存儲從此關鍵幀開始的換轉指標。

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
