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
ms.openlocfilehash: d36c924d30bd728fcd54b6cdf6805ade25e20b5c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296601"
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
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|建構主要畫面格物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|加入分鏡腳本主要畫面格。|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|傳回基礎主要畫面格的值。|
|[CBaseKeyFrame::IsAdded](#isadded)|會告知是否已加入主要畫面格分鏡腳本。|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|指定是否應分鏡腳本的位移，或在轉換之後加入主要畫面格。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|指定是否已加入此主要畫面格的分鏡腳本。|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定這個主要畫面格是否應新增至現有的主要畫面格另一個，從位移處或結尾的某些轉換分鏡腳本。|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|表示 Windows 動畫 API 主要畫面格。 主要畫面格不在初始化時則會將它設定為預先定義的值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。|

## <a name="remarks"></a>備註

封裝 UI_ANIMATION_KEYFRAME 變數。 如果需要做的任何主要畫面格實作的基底類別。 主要畫面格代表時間的分鏡腳本內的時間點，而且可用來指定開始和結束時間的轉換。 有兩種類型的主要畫面格-主要畫面格加入至分鏡腳本中指定的位移 （以時間） 或加入指定的轉換後的主要畫面格。 因為動畫開始之前，無法知道的某些轉換持續時間，所以某些主要畫面格的實際值會決定在執行階段只。 因為主要畫面格可能取決於轉換，取決於主要畫面格，而在其開啟，所以務必建置主要畫面格鏈結時，防止無限遞迴。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard

加入分鏡腳本主要畫面格。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>參數

*pStoryboard*<br/>
分鏡腳本指標。

*bDeepAdd*<br/>
如果此參數為 TRUE，且要加入主要畫面格取決於其他主要畫面格或轉換，這個方法會嘗試加入此主要畫面格或轉為分鏡腳本第一次。

### <a name="return-value"></a>傳回值

如果主要畫面格新增到分鏡腳本成功;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

將分鏡腳本主要畫面格，會呼叫這個方法。

##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame

建構主要畫面格物件。

```
CBaseKeyFrame();
```

##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe

傳回基礎主要畫面格的值。

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>傳回值

目前的主要畫面格。 預設值是 UI_ANIMATION_KEYFRAME_STORYBOARD_START。

### <a name="remarks"></a>備註

這是為基礎的主要畫面格值存取子。

##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded

會告知是否已加入主要畫面格分鏡腳本。

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>傳回值

如果主要畫面格會新增至分鏡腳本，則為 TRUE則為 FALSE。

### <a name="remarks"></a>備註

基底類別中 IsAdded 一定會傳回 TRUE，但它在衍生類別中覆寫。

##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset

指定是否應分鏡腳本的位移，或在轉換之後加入主要畫面格。

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>傳回值

如果主要畫面格應該新增到分鏡腳本中某些指定的位移，則為 TRUE。 如果主要畫面格應該加入一些轉換後的分鏡腳本，則為 FALSE。

### <a name="remarks"></a>備註

指定是否應加入主要畫面格位移分鏡腳本。 必須在衍生類別中指定的位移或轉換。

##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded

指定是否已加入此主要畫面格的分鏡腳本。

```
BOOL m_bAdded;
```

##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset

指定這個主要畫面格是否應新增至現有的主要畫面格另一個，從位移處或結尾的某些轉換分鏡腳本。

```
BOOL m_bIsKeyframeAtOffset;
```

##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe

表示 Windows 動畫 API 主要畫面格。 主要畫面格不在初始化時則會將它設定為預先定義的值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
