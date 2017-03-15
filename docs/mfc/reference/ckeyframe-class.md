---
title: "CKeyFrame 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CKeyFrame
- CKeyFrame
dev_langs:
- C++
helpviewer_keywords:
- CKeyFrame class
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 18
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
ms.openlocfilehash: d8ecff2e36148fb114ee708712b6e8bd0fe558ed
ms.lasthandoff: 02/24/2017

---
# <a name="ckeyframe-class"></a>CKeyFrame 類別
表示動畫主要畫面格。  
  
## <a name="syntax"></a>語法  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](#ckeyframe)|多載。 建構主要畫面格相依於其他主要畫面格。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|將主要畫面格加入至分鏡腳本。 (覆寫[CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|加入分鏡腳本完成轉換之後的主要畫面格。|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|加入主要畫面格位移分鏡腳本。|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|傳回這個主要畫面格取決於主要畫面格的指標。|  
|[CKeyFrame::GetOffset](#getoffset)|傳回從其他主要畫面格的位移。|  
|[CKeyFrame::GetTransition](#gettransition)|傳回的指標轉換，取決於此主要畫面格。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|指定從主要畫面格 m_pExistingKeyFrame 中儲存此主要畫面格的位移。|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|儲存至現有的 keframe 的指標。 此主要畫面格加入與現有的主要畫面格 m_offset 分鏡腳本。|  
|[CKeyFrame::m_pTransition](#m_ptransition)|儲存的指標來開始這個主要畫面格的轉換。|  
  
## <a name="remarks"></a>備註  
 這個類別會實作動畫主要畫面格。 主要畫面格代表一個時間點內的分鏡腳本的時間，而且可用來指定轉換的開始和結束時間。 主要畫面格可能根據其他主要畫面格的位移 （以秒為單位），或可能根據轉換，以及擁有代表這項轉換結束時的時間點。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-nameaddtostoryboarda--ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard  
 將主要畫面格加入至分鏡腳本。  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本指標。  
  
 `bDeepAdd`  
 指定是否要加入主要畫面格，或轉換以遞迴方式。  
  
### <a name="return-value"></a>傳回值  
 如果為 TRUE，成功加入主要畫面格。  
  
### <a name="remarks"></a>備註  
 這個方法會加入至分鏡腳本主要畫面格。 如果它相依於其他主要畫面格或轉換 bDeepAdd 為 TRUE，這個方法會嘗試以遞迴方式加入。  
  
##  <a name="a-nameaddtostoryboardaftertransitiona--ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition  
 加入分鏡腳本完成轉換之後的主要畫面格。  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本指標。  
  
 `bDeepAdd`  
 指定是否要轉換以遞迴方式加入。  
  
### <a name="return-value"></a>傳回值  
 如果為 TRUE，成功加入主要畫面格。  
  
### <a name="remarks"></a>備註  
 架構以新增主要畫面格分鏡腳本完成轉換之後會呼叫此函式。  
  
##  <a name="a-nameaddtostoryboardatoffseta--ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset  
 加入主要畫面格位移分鏡腳本。  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本指標。  
  
 `bDeepAdd`  
 指定是否要加入主要畫面格至此主要畫面格定以遞迴方式。  
  
### <a name="return-value"></a>傳回值  
 如果為 TRUE，成功加入主要畫面格。  
  
### <a name="remarks"></a>備註  
 此函式會呼叫架構以新增至腳本位移主要畫面格。  
  
##  <a name="a-nameckeyframea--ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame  
 建構取決於轉換的主要畫面格。  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>參數  
 `pTransition`  
 轉換指標。  
  
 `pKeyframe`  
 主要畫面格指標。  
  
 `offset`  
 以秒為單位，從主要畫面格 pKeyframe 所指定的位移。  
  
### <a name="remarks"></a>備註  
 指定的轉換結束時，建構的主要畫面格會呈現在腳本內的時間點。  
  
##  <a name="a-namegetexistingkeyframea--ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe  
 傳回這個主要畫面格取決於主要畫面格的指標。  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>傳回值  
 主要畫面格或如果此主要畫面格不相依於其他主要畫面格則為 NULL 的有效指標。  
  
### <a name="remarks"></a>備註  
 這是取決於此主要畫面格的主要畫面格的存取子。  
  
##  <a name="a-namegetoffseta--ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset  
 傳回從其他主要畫面格的位移。  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>傳回值  
 以秒為單位，從其他主要畫面格的位移。  
  
### <a name="remarks"></a>備註  
 若要判斷位移 （秒） 從其他主要畫面格，應該呼叫這個方法。  
  
##  <a name="a-namegettransitiona--ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition  
 傳回的指標轉換，取決於此主要畫面格。  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>傳回值  
 有效的指標轉換，或如果此主要畫面格不會根據轉換為 NULL。  
  
### <a name="remarks"></a>備註  
 這是轉換，取決於此主要畫面格的存取子。  
  
##  <a name="a-namemoffseta--ckeyframemoffset"></a><a name="m_offset"></a>CKeyFrame::m_offset  
 指定從主要畫面格 m_pExistingKeyFrame 中儲存此主要畫面格的位移。  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="a-namempexistingkeyframea--ckeyframempexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame  
 儲存至現有的 keframe 的指標。 此主要畫面格加入與現有的主要畫面格 m_offset 分鏡腳本。  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="a-namemptransitiona--ckeyframemptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition  
 儲存的指標來開始這個主要畫面格的轉換。  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

