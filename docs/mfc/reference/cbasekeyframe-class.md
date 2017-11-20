---
title: "CBaseKeyFrame 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae23fabc33d744265677e395310ba1f14dcb64ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|建構主要畫面格的物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|加入分鏡腳本主要畫面格。|  
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|傳回基礎主要畫面格的值。|  
|[CBaseKeyFrame::IsAdded](#isadded)|告知一個主要畫面格是否已加入至分鏡腳本。|  
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|指定是否應加入主要畫面格位移，或轉換之後，分鏡腳本。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseKeyFrame::m_bAdded](#m_badded)|指定是否已加入這個主要畫面格的分鏡腳本。|  
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|指定這個主要畫面格是否應加入至分鏡腳本的位移，從現有的主要畫面格另一個，或結尾的某些轉換。|  
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|代表 Windows 動畫 API 的主要畫面格。 當主要畫面格未初始化它是設定為預先定義的值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。|  
  
## <a name="remarks"></a>備註  
 封裝 UI_ANIMATION_KEYFRAME 變數。 可做為主要畫面格的任何實作的基底類別。 主要畫面格代表一個時間點內的分鏡腳本的時間，而且可用來指定的開始和結束時間的轉換。 有兩種類型的主要畫面格的主要畫面格加入至分鏡腳本於指定位移 （以時間表示） 或加入指定的轉換後的主要畫面格。 動畫啟動之前無法知道的某些轉換持續時間，因為某些主要畫面格的實際值會決定在執行階段只。 因為主要畫面格可能會取決於轉換，這在其取決於主要畫面格，務必建立主要畫面格鏈結時，防止無限遞迴。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseKeyFrame`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard  
 加入分鏡腳本主要畫面格。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本指標。  
  
 `bDeepAdd`  
 如果此參數為 TRUE，而且要加入的主要畫面格取決於其他主要畫面格或轉換，這個方法會嘗試加入這個主要畫面格或轉為分鏡腳本第一次。  
  
### <a name="return-value"></a>傳回值  
 主要畫面格已加入至分鏡腳本已成功; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是將分鏡腳本主要畫面格。  
  
##  <a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame  
 建構主要畫面格的物件。  
  
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
 這是為基礎的主要畫面格值存取子。  
  
##  <a name="isadded"></a>CBaseKeyFrame::IsAdded  
 告知一個主要畫面格是否已加入至分鏡腳本。  
  
```  
BOOL IsAdded() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果主要畫面格加入至分鏡腳本，則為 TRUE則為 FALSE。  
  
### <a name="remarks"></a>備註  
 基底類別中 IsAdded 一定會傳回 TRUE，但會在衍生類別中覆寫。  
  
##  <a name="iskeyframeatoffset"></a>CBaseKeyFrame::IsKeyframeAtOffset  
 指定是否應加入主要畫面格位移，或轉換之後，分鏡腳本。  
  
```  
BOOL IsKeyframeAtOffset() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果主要畫面格應該加入至某些指定之位移分鏡腳本，則為 TRUE。 如果主要畫面格應該加入至分鏡腳本後一些轉換，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 指定是否應加入主要畫面格位移分鏡腳本。 必須在衍生類別中指定的位移或轉換。  
  
##  <a name="m_badded"></a>CBaseKeyFrame::m_bAdded  
 指定是否已加入這個主要畫面格的分鏡腳本。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset  
 指定這個主要畫面格是否應加入至分鏡腳本的位移，從現有的主要畫面格另一個，或結尾的某些轉換。  
  
```  
BOOL m_bIsKeyframeAtOffset;  
```  
  
##  <a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe  
 代表 Windows 動畫 API 的主要畫面格。 當主要畫面格未初始化它是設定為預先定義的值 UI_ANIMATION_KEYFRAME_STORYBOARD_START。  
  
```  
UI_ANIMATION_KEYFRAME m_keyframe;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
