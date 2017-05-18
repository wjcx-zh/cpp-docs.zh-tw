---
title: "CAnimationGroup 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationGroup class
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a59d8a86fde68510d48e4a3398b6590b2215cbea
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="canimationgroup-class"></a>CAnimationGroup 類別
實作動畫群組，也就是結合動畫腳本動畫物件，來定義動畫的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationGroup;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|建構動畫群組。|  
|[CAnimationGroup:: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|解構函式。 動畫群組終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::Animate](#animate)|動畫的群組。|  
|[CAnimationGroup::ApplyTransitions](#applytransitions)|套用至動畫物件的轉換。|  
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|尋找包含指定的動畫變數的動畫物件。|  
|[CAnimationGroup::GetGroupID](#getgroupid)|傳回 GroupID。|  
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|移除，並選擇性地會終結所有主要畫面格動畫群組。|  
|[CAnimationGroup::RemoveTransitions](#removetransitions)|移除屬於群組的動畫的動畫物件的轉換。|  
|[CAnimationGroup::Schedule](#schedule)|排程在指定時間的動畫。|  
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|指示所有動畫物件屬於群組會自動都終結轉換。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](#addkeyframes)|加入主要畫面格的分鏡腳本協助程式。|  
|[CAnimationGroup::AddTransitions](#addtransitions)|將轉換加入至分鏡腳本協助程式。|  
|[CAnimationGroup::CreateTransitions](#createtransitions)|建立轉換的 COM 物件的 helper。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除轉換的動畫物件屬於群組。 這個成員是 TRUE，如果轉換會在動畫已排定自動移除。 否則，您必須手動移除轉換。|  
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定要終結動畫物件的方式。 如果此參數為 TRUE，動畫物件將會自動終結時終結該群組。 否則必須以手動方式終結動畫的物件。 預設值為 FALSE。 此值設定為 TRUE，只有當所有動畫物件屬於群組會以動態方式都配置使用 new 運算子。|  
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定要終結的主要畫面格的方式。 如果此值為 TRUE，會移除所有主要畫面格，並終結;否則，則會移除從僅限清單。 預設值為 TRUE。|  
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|包含動畫物件的清單。|  
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|包含一份主要畫面格。|  
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|指向以動畫腳本。 只有在動畫上呼叫之後，這個指標是有效。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|動畫群組的唯一識別項。|  
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|此群組所屬的動畫控制器指標。|  
  
## <a name="remarks"></a>備註  
 當您新增動畫物件使用 CAnimationController::AddAnimationObject 動畫群組就會自動建立動畫控制站 (CAnimationController)。 動畫群組識別碼，通常是採取操作動畫群組做為參數來識別。 識別碼是取自第一次的動畫物件新增至新的動畫群組。 之後，您呼叫 CAnimationController::AnimateGroup，而且可以透過公用成員 m_pStoryboard 存取建立封裝的動畫腳本。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CAnimationGroup`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationgroup"></a>CAnimationGroup:: ~ CAnimationGroup  
 解構函式。 動畫群組終結時呼叫。  
  
```  
~CAnimationGroup();
```  
  
##  <a name="addkeyframes"></a>CAnimationGroup::AddKeyframes  
 加入主要畫面格的分鏡腳本協助程式。  
  
```  
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 腳本 COM 物件的指標。  
  
 `bAddDeep`  
 指定這個方法應該加入相依於其他主要畫面格的分鏡腳本主要畫面格。  
  
##  <a name="addtransitions"></a>CAnimationGroup::AddTransitions  
 將轉換加入至分鏡腳本協助程式。  
  
```  
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 腳本 COM 物件的指標。  
  
 `bDependOnKeyframes`  
  
##  <a name="animate"></a>CAnimationGroup::Animate  
 動畫的群組。  
  
```  
BOOL Animate(
    IUIAnimationManager* pManager,  
    IUIAnimationTimer* pTimer,  
    BOOL bScheduleNow);
```  
  
### <a name="parameters"></a>參數  
 `pManager`  
 `pTimer`  
 `bScheduleNow`  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會建立內部的分鏡腳本、 建立和套用轉換和排程動畫 bScheduleNow 結果為 TRUE。 如果 bScheduleNow 是 FALSE，您需要呼叫啟動動畫在指定的時間排程。  
  
##  <a name="applytransitions"></a>CAnimationGroup::ApplyTransitions  
 套用至動畫物件的轉換。  
  
```  
void ApplyTransitions();
```  
  
### <a name="remarks"></a>備註  
 這個方法會判斷提示偵錯模式中如果不建立分鏡腳本。 它首先，建立所有的轉換，然後加入 「 靜態 」 的主要畫面格 （主要畫面格位移而定）、 加入轉換，而不必主要畫面格，加入主要畫面格根據轉換和其他主要畫面格，然後在上一次加入取決於主要畫面格的轉換。  
  
##  <a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup  
 建構動畫群組。  
  
```  
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```  
  
### <a name="parameters"></a>參數  
 `pParentController`  
 動畫控制器可建立一組指標。  
  
 `nGroupID`  
 指定識別碼。  
  
##  <a name="createtransitions"></a>CAnimationGroup::CreateTransitions  
 建立轉換的 COM 物件的 helper。  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>傳回值  
 此方法成功，否則為 FALSE 則為 TRUE。  
  
##  <a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject  
 尋找包含指定的動畫變數的動畫物件。  
  
```  
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>參數  
 `pVariable`  
 動畫變數的指標。  
  
### <a name="return-value"></a>傳回值  
 動畫物件或 NULL，如果找不到動畫物件的指標。  
  
##  <a name="getgroupid"></a>CAnimationGroup::GetGroupID  
 傳回 GroupID。  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 群組識別碼。  
  
##  <a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions  
 指定如何清除轉換的動畫物件屬於群組。 這個成員是 TRUE，如果轉換會在動畫已排定自動移除。 否則，您必須手動移除轉換。  
  
```  
BOOL m_bAutoclearTransitions;  
```  
  
##  <a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects  
 指定要終結動畫物件的方式。 如果此參數為 TRUE，動畫物件將會自動終結時終結該群組。 否則必須以手動方式終結動畫的物件。 預設值為 FALSE。 此值設定為 TRUE，只有當所有動畫物件屬於群組會以動態方式都配置使用 new 運算子。  
  
```  
BOOL m_bAutodestroyAnimationObjects;  
```  
  
##  <a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes  
 指定要終結的主要畫面格的方式。 如果此值為 TRUE，會移除所有主要畫面格，並終結;否則，則會移除從僅限清單。 預設值為 TRUE。  
  
```  
BOOL m_bAutodestroyKeyframes;  
```  
  
##  <a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects  
 包含動畫物件的清單。  
  
```  
CObList m_lstAnimationObjects;  
```  
  
##  <a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames  
 包含一份主要畫面格。  
  
```  
CObList m_lstKeyFrames;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID  
 動畫群組的唯一識別項。  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController  
 此群組所屬的動畫控制器指標。  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard  
 指向以動畫腳本。 只有在動畫上呼叫之後，這個指標是有效。  
  
```  
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;  
```  
  
##  <a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes  
 移除，並選擇性地會終結所有主要畫面格動畫群組。  
  
```  
void RemoveKeyframes();
```  
  
### <a name="remarks"></a>備註  
 如果 m_bAutodestroyKeyframes 成員則為 TRUE，則會移除主要畫面格，並將其終結，否則主要畫面格只會移除從內部清單中的主要畫面格。  
  
##  <a name="removetransitions"></a>CAnimationGroup::RemoveTransitions  
 移除屬於群組的動畫的動畫物件的轉換。  
  
```  
void RemoveTransitions();
```  
  
### <a name="remarks"></a>備註  
 如果 m_bAutoclearTransitions 旗標設為 TRUE 時，這個方法屬於該群組的所有動畫物件進行都迴圈，並且呼叫 CAnimationObject::ClearTransitions(FALSE)。  
  
##  <a name="schedule"></a>CAnimationGroup::Schedule  
 排程在指定時間的動畫。  
  
```  
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```  
  
### <a name="parameters"></a>參數  
 `pTimer`  
 動畫計時器指標。  
  
 `time`  
 指定排程動畫的時間。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則為 TRUEFALSE 如果方法失敗，或如果動畫尚未呼叫與 bScheduleNow 設為 FALSE。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可排程於指定時間的動畫。 您必須呼叫動畫與 bScheduleNow 先設為 FALSE。  
  
##  <a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions  
 指示所有動畫物件屬於群組會自動都終結轉換。  
  
```  
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bAutoDestroy`  
 指定要終結的轉換方式。  
  
### <a name="remarks"></a>備註  
 您可以將此值設為 FALSE，只有當您配置在堆疊上的轉換。 預設值為 TRUE，因此強烈建議您先配置轉換物件，使用新的運算子。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

