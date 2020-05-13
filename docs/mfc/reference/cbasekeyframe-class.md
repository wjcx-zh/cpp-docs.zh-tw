---
title: CBaseKeyFrame 類別
ms.date: 11/04/2016
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352994"
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame 類別

實作主要畫面格的基本功能。

## <a name="syntax"></a>語法

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBaseKey 框架:C基鍵框架](#cbasekeyframe)|構造關鍵幀物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBaseKeyFrame::新增故事板](#addtostoryboard)|將關鍵幀添加到情節提要。|
|[CBase 鍵框:獲取動畫關鍵幀](#getanimationkeyframe)|返回基礎關鍵幀值。|
|[CBaseKey 框架:已新增](#isadded)|告訴是否已將關鍵幀添加到情節提要中。|
|[CBaseKey框架:是關鍵幀幀偏移](#iskeyframeatoffset)|指定關鍵幀是否應在偏移時或過渡後添加到情節提要。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CBaseKey框架::m_bAdded](#m_badded)|指定此關鍵幀是否已添加到情節提要。|
|[CBaseKeyFrame:m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定是否應將此關鍵幀添加到與另一個現有關鍵幀偏移量或某些轉換結束時的情節提要。|
|[CBaseKeyFrame:m_keyframe](#m_keyframe)|表示 Windows 動畫 API 關鍵幀。 未初始化關鍵幀時,它將設置為預定義值UI_ANIMATION_KEYFRAME_STORYBOARD_START。|

## <a name="remarks"></a>備註

封裝UI_ANIMATION_KEYFRAME變數。 用作任何關鍵幀實現的基類。 關鍵幀表示情節提要中的一個時刻,可用於指定過渡的開始和結束時間。 有兩種類型的關鍵幀 - 在指定的偏移量(時間)添加到情節提要的關鍵幀,或指定轉換后添加的關鍵幀。 由於某些轉換的持續時間在動畫啟動之前無法知道,因此某些關鍵幀的實際值僅在運行時確定。 由於關鍵幀可能依賴於過渡(而過渡又取決於關鍵幀,因此在構建關鍵幀鏈時防止無限遞歸非常重要。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame::新增故事板

將關鍵幀添加到情節提要。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標。

*bDeepAdd*<br/>
如果此參數為 TRUE,並且要添加的關鍵幀取決於其他關鍵幀或轉換,則此方法將嘗試先添加此關鍵幀或轉換為情節提要。

### <a name="return-value"></a>傳回值

如果關鍵幀已成功添加到情節提要,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

調用此方法是為了向情節提要添加關鍵幀。

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKey 框架:C基鍵框架

構造關鍵幀物件。

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBase 鍵框:獲取動畫關鍵幀

返回基礎關鍵幀值。

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>傳回值

當前關鍵幀。 默認值為UI_ANIMATION_KEYFRAME_STORYBOARD_START。

### <a name="remarks"></a>備註

這是對基礎關鍵幀值的訪問器。

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CBaseKey 框架:已新增

告訴是否已將關鍵幀添加到情節提要中。

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>傳回值

如果關鍵幀已添加到情節提要,則為 TRUE;奧特威斯·法爾。

### <a name="remarks"></a>備註

在基類 Is添加中始終返回 TRUE,但在派生類中重寫 TRUE。

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CBaseKey框架:是關鍵幀幀偏移

指定關鍵幀是否應在偏移時或過渡後添加到情節提要。

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>傳回值

如果關鍵幀應添加到情節提要,在某些指定的偏移量。 如果關鍵幀應在一些轉換后添加到情節提要中,則 FALSE。

### <a name="remarks"></a>備註

指定是否應在偏移量下將關鍵幀添加到情節提要。 偏移量或過渡必須在派生類中指定。

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKey框架::m_bAdded

指定此關鍵幀是否已添加到情節提要。

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame:m_bIsKeyframeAtOffset

指定是否應將此關鍵幀添加到與另一個現有關鍵幀偏移量或某些轉換結束時的情節提要。

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame:m_keyframe

表示 Windows 動畫 API 關鍵幀。 未初始化關鍵幀時,它將設置為預定義值UI_ANIMATION_KEYFRAME_STORYBOARD_START。

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
