---
title: CAnimationGroup 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11b78cf273fd510b8ce224004c759dcc5bbe3bec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355629"
---
# <a name="canimationgroup-class"></a>CAnimationGroup 類別
實作動畫群組，其結合了動畫分鏡腳本動畫物件，定義動畫的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationGroup;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|建構動畫群組。|  
|[CAnimationGroup:: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|解構函式。 當動畫群組正在被終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::Animate](#animate)|以動畫顯示的群組。|  
|[CAnimationGroup::ApplyTransitions](#applytransitions)|套用至動畫物件的轉換。|  
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|尋找包含指定的動畫變數的動畫物件。|  
|[CAnimationGroup::GetGroupID](#getgroupid)|傳回 GroupID。|  
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|移除，並選擇性地會終結所有主要畫面格屬於群組的動畫。|  
|[CAnimationGroup::RemoveTransitions](#removetransitions)|移除屬於群組的動畫的動畫物件的轉換。|  
|[CAnimationGroup::Schedule](#schedule)|排程在指定時間的動畫。|  
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|會指示所有動畫物件屬於群組會自動都終結轉換。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](#addkeyframes)|加入主要畫面格的分鏡腳本 helper。|  
|[CAnimationGroup::AddTransitions](#addtransitions)|將轉換加入至分鏡腳本 helper。|  
|[CAnimationGroup::CreateTransitions](#createtransitions)|建立轉換的 COM 物件的 helper。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除從屬於群組的動畫物件的轉換。 如果這個成員為 TRUE 時，轉換會在已排定動畫時自動移除。 否則，您必須手動移除轉換。|  
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定要終結動畫物件的方式。 如果此參數為 TRUE，動畫物件將會自動終結時終結該群組。 否則必須以手動方式終結動畫物件。 預設值為 FALSE。 此值設定為 TRUE，只有當屬於群組的所有動畫物件將以動態方式都配置使用 new 運算子。|  
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定要終結的主要畫面格的方式。 如果此值為 TRUE 時，會移除所有主要畫面格，並終結;否則，它們會移除從僅限清單。 預設值為 TRUE。|  
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|包含動畫物件的清單。|  
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|包含主要畫面格的清單。|  
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|動畫的分鏡腳本的點。 此指標上動畫呼叫後才是有效的。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|動畫群組的唯一識別碼。|  
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|此群組所屬的動畫控制器指標。|  
  
## <a name="remarks"></a>備註  
 當您新增使用 CAnimationController::AddAnimationObject 動畫物件時，動畫群組會自動建立動畫控制站 (CAnimationController)。 動畫群組識別碼，通常採用操作動畫群組做為參數來識別。 GroupID 取自第一次的動畫物件加入至新的動畫群組。 您可以呼叫 CAnimationController::AnimateGroup 並可透過公用成員 m_pStoryboard 存取之後，會建立封裝的動畫分鏡腳本。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CAnimationGroup`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup:: ~ CAnimationGroup  
 解構函式。 當動畫群組正在被終結時呼叫。  
  
```  
~CAnimationGroup();
```  
  
##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes  
 加入主要畫面格的分鏡腳本 helper。  
  
```  
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本 COM 物件的指標。  
  
 `bAddDeep`  
 指定此方法是否應將取決於其他主要畫面格的分鏡腳本主要畫面格。  
  
##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions  
 將轉換加入至分鏡腳本 helper。  
  
```  
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本 COM 物件的指標。  
  
 `bDependOnKeyframes`  
  
##  <a name="animate"></a>  CAnimationGroup::Animate  
 以動畫顯示的群組。  
  
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
 如果方法成功則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會建立內部的分鏡腳本、 建立和套用轉換，若為 TRUE，否則 bScheduleNow 排程動畫。 如果 bScheduleNow 為 FALSE 時，您需要呼叫排程開始的指定時間的動畫。  
  
##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions  
 套用至動畫物件的轉換。  
  
```  
void ApplyTransitions();
```  
  
### <a name="remarks"></a>備註  
 這個方法會判斷提示偵錯模式中如果不建立分鏡腳本。 它首先，建立所有轉換，然後新增 「 靜態 」 的主要畫面格 （主要畫面格相依於位移）、 加入不相依於主要畫面格的轉換，將根據轉換的主要畫面格和其他主要畫面格，然後在上一次加入取決於主要畫面格的轉換.  
  
##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup  
 建構動畫群組。  
  
```  
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```  
  
### <a name="parameters"></a>參數  
 `pParentController`  
 動畫控制器可建立一組指標。  
  
 `nGroupID`  
 指定 GroupID。  
  
##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions  
 建立轉換的 COM 物件的 helper。  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>傳回值  
 此方法成功，否則為 FALSE，則為 TRUE。  
  
##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject  
 尋找包含指定的動畫變數的動畫物件。  
  
```  
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>參數  
 `pVariable`  
 動畫變數的指標。  
  
### <a name="return-value"></a>傳回值  
 動畫物件或如果找不到動畫物件為 NULL 指標。  
  
##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID  
 傳回 GroupID。  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 群組識別碼。  
  
##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions  
 指定如何清除從屬於群組的動畫物件的轉換。 如果這個成員為 TRUE 時，轉換會在已排定動畫時自動移除。 否則，您必須手動移除轉換。  
  
```  
BOOL m_bAutoclearTransitions;  
```  
  
##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects  
 指定要終結動畫物件的方式。 如果此參數為 TRUE，動畫物件將會自動終結時終結該群組。 否則必須以手動方式終結動畫物件。 預設值為 FALSE。 此值設定為 TRUE，只有當屬於群組的所有動畫物件將以動態方式都配置使用 new 運算子。  
  
```  
BOOL m_bAutodestroyAnimationObjects;  
```  
  
##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes  
 指定要終結的主要畫面格的方式。 如果此值為 TRUE 時，會移除所有主要畫面格，並終結;否則，它們會移除從僅限清單。 預設值為 TRUE。  
  
```  
BOOL m_bAutodestroyKeyframes;  
```  
  
##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects  
 包含動畫物件的清單。  
  
```  
CObList m_lstAnimationObjects;  
```  
  
##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames  
 包含主要畫面格的清單。  
  
```  
CObList m_lstKeyFrames;  
```  
  
##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID  
 動畫群組的唯一識別碼。  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController  
 此群組所屬的動畫控制器指標。  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard  
 動畫的分鏡腳本的點。 此指標上動畫呼叫後才是有效的。  
  
```  
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;  
```  
  
##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes  
 移除，並選擇性地會終結所有主要畫面格屬於群組的動畫。  
  
```  
void RemoveKeyframes();
```  
  
### <a name="remarks"></a>備註  
 如果 m_bAutodestroyKeyframes 成員為 TRUE，則會移除主要畫面格，並終結，否則主要畫面格只會移除從內部的主要畫面格的清單。  
  
##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions  
 移除屬於群組的動畫的動畫物件的轉換。  
  
```  
void RemoveTransitions();
```  
  
### <a name="remarks"></a>備註  
 如果 m_bAutoclearTransitions 旗標設定為 TRUE 時，這個方法會透過屬於該群組的所有動畫物件執行迴圈，並呼叫 CAnimationObject::ClearTransitions(FALSE)。  
  
##  <a name="schedule"></a>  CAnimationGroup::Schedule  
 排程在指定時間的動畫。  
  
```  
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```  
  
### <a name="parameters"></a>參數  
 `pTimer`  
 動畫計時器指標。  
  
 `time`  
 指定排程動畫時間。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為 TRUEFALSE 如果方法失敗，或以動畫顯示如果尚未呼叫與 bScheduleNow 設為 FALSE。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可排程在指定時間的動畫。 您必須先設為 FALSE 的 bScheduleNow 與呼叫動畫。  
  
##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions  
 會指示所有動畫物件屬於群組會自動都終結轉換。  
  
```  
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bAutoDestroy`  
 指定要終結的轉換方式。  
  
### <a name="remarks"></a>備註  
 您可以將此值設為 FALSE，只有當您配置在堆疊上的轉換。 預設值為 TRUE，因此強烈建議您配置轉換物件使用新的運算子。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
