---
title: "CBaseKeyFrame 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CBaseKeyFrame class
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cfbaac379097c89b5dcb52fa36c0cd1f6e3d2c7f
ms.lasthandoff: 02/24/2017

---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame 類別
實作主要畫面格的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|建構主要畫面格物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|加入主要畫面格分鏡腳本。|  
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|傳回基礎主要畫面格的值。|  
|[CBaseKeyFrame::IsAdded](#isadded)|會指示是否已加入主要畫面格分鏡腳本。|  
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|指定是否應加入主要畫面格位移，或在轉換之後，分鏡腳本。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseKeyFrame::m_bAdded](#m_badded)|指定是否已加入至此主要畫面格的分鏡腳本。|  
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定是否應分鏡腳本開頭的位移，從另一個現有主要畫面格，或在某些轉換結尾處加入這個主要畫面格。|  
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|代表 Windows 動畫 API 主要畫面格。 當未初始化的主要畫面格系統是設定為預先定義的值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。|  
  
## <a name="remarks"></a>備註  
 封裝 UI_ANIMATION_KEYFRAME 變數。 做為任何主要畫面格實作的基底類別。 主要畫面格代表一個時間點內的分鏡腳本的時間，而且可用來指定轉換的開始和結束時間。 有兩種類型的主要畫面格的主要畫面格加入至分鏡腳本中指定的位移 （以時間） 或加入指定的轉換後的主要畫面格。 因為無法知道的某些轉換持續時間，動畫開始之前，在執行階段才決定的一些主要畫面格實際值。 因為主要畫面格可能相依於轉換，轉而在相依於主要畫面格，務必建立主要畫面格鏈結時，防止無限遞迴。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseKeyFrame`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard  
 加入主要畫面格分鏡腳本。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本指標。  
  
 `bDeepAdd`  
 如果此參數為 TRUE，而且要加入主要畫面格取決於一些其他的主要畫面格或轉換，這個方法會嘗試將此主要畫面格或轉為分鏡腳本第一次。  
  
### <a name="return-value"></a>傳回值  
 如果成功，分鏡腳本加入主要畫面格，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您可以呼叫這個方法加入至分鏡腳本主要畫面格。  
  
##  <a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame  
 建構主要畫面格物件。  
  
```  
CBaseKeyFrame();
```  
  
##  <a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe  
 傳回基礎主要畫面格的值。  
  
```  
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的主要畫面格。 預設值是 UI_ANIMATION_KEYFRAME_STORYBOARD_START。  
  
### <a name="remarks"></a>備註  
 這是為基礎的主要畫面格值的存取子。  
  
##  <a name="isadded"></a>CBaseKeyFrame::IsAdded  
 會指示是否已加入主要畫面格分鏡腳本。  
  
```  
BOOL IsAdded() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果主要畫面格加入至腳本，則為 TRUE則為 FALSE。  
  
### <a name="remarks"></a>備註  
 基底類別中 IsAdded 一定會傳回 TRUE，但在衍生類別中覆寫。  
  
##  <a name="iskeyframeatoffset"></a>CBaseKeyFrame::IsKeyframeAtOffset  
 指定是否應加入主要畫面格位移，或在轉換之後，分鏡腳本。  
  
```  
BOOL IsKeyframeAtOffset() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果主要畫面格應該加入至分鏡腳本中某些指定的位移，則為 TRUE。 如果主要畫面格應該加入至分鏡腳本某些轉換之後，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 指定是否應加入主要畫面格位移分鏡腳本。 必須在衍生類別中指定的位移或轉換。  
  
##  <a name="m_badded"></a>CBaseKeyFrame::m_bAdded  
 指定是否已加入至此主要畫面格的分鏡腳本。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset  
 指定是否應分鏡腳本開頭的位移，從另一個現有主要畫面格，或在某些轉換結尾處加入這個主要畫面格。  
  
```  
BOOL m_bIsKeyframeAtOffset;  
```  
  
##  <a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe  
 代表 Windows 動畫 API 主要畫面格。 當未初始化的主要畫面格系統是設定為預先定義的值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。  
  
```  
UI_ANIMATION_KEYFRAME m_keyframe;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

