---
title: CAnimationGroup 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 9be0a5b76f91ddf4dc3d1c4ff2816b7ffd5a1986
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304375"
---
# <a name="canimationgroup-class"></a>CAnimationGroup 類別

實作動畫群組，結合了動畫腳本、 動畫物件和轉換來定義動畫。

## <a name="syntax"></a>語法

```
class CAnimationGroup;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|建構的動畫群組。|
|[CAnimationGroup::~CAnimationGroup](#canimationgroup__~canimationgroup)|解構函式。 當動畫群組正在被終結時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|以動畫顯示的群組。|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|轉換會套用至動畫物件。|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|尋找包含指定的動畫變數的動畫物件。|
|[CAnimationGroup::GetGroupID](#getgroupid)|會傳回 GroupID。|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|移除，並選擇性地會終結所有主要畫面格屬於群組的動畫。|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|移除屬於群組的動畫的動畫物件的轉換。|
|[CAnimationGroup::Schedule](#schedule)|排程在指定時間的動畫。|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|指示屬於自動群組的所有動畫物件都終結轉換。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|協助程式新增主要畫面格的分鏡腳本。|
|[CAnimationGroup::AddTransitions](#addtransitions)|將轉換加入至分鏡腳本 helper。|
|[CAnimationGroup::CreateTransitions](#createtransitions)|建立轉換的 COM 物件的 helper。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除從屬於群組的動畫物件的轉換。 如果這個成員為 TRUE 時，轉換會在動畫已排程時自動移除。 否則，您必須手動移除轉換。|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定要終結動畫物件的方式。 如果此參數為 TRUE，動畫物件將會自動終結時終結該群組。 否則必須以手動方式終結動畫物件。 預設值為 FALSE。 設定此值設為 TRUE，才是屬於群組的所有動畫物件以動態方式都配置，使用 new 運算子。|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定要終結的主要畫面格的方式。 如果此值為 TRUE，會移除所有的主要畫面格，並終結;否則，則會移除從僅限的清單。 預設值為 TRUE。|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|包含一份動畫物件。|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|包含主要畫面格的清單。|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|指向動畫腳本。 只有在動畫上呼叫之後，這個指標是有效。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|動畫群組的唯一識別碼。|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|此群組所屬的動畫控制器指標。|

## <a name="remarks"></a>備註

當您新增使用 CAnimationController::AddAnimationObject 的動畫物件時，動畫群組會自動建立動畫控制器 (CAnimationController)。 動畫群組會識別 GroupID，通常會做為參數來操作動畫群組。 擁有的 GroupID 取自第一次的動畫物件新增至新的動畫群組。 您呼叫 CAnimationController::AnimateGroup，而且可以透過 public 成員 m_pStoryboard 存取之後，會建立封裝的動畫腳本。

## <a name="inheritance-hierarchy"></a>繼承階層

`CAnimationGroup`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup::~CAnimationGroup

解構函式。 當動畫群組正在被終結時呼叫。

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

協助程式新增主要畫面格的分鏡腳本。

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>參數

*pStoryboard*<br/>
分鏡腳本 COM 物件的指標。

*bAddDeep*<br/>
指定此方法應該加入相依於其他主要畫面格的分鏡腳本主要畫面格。

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

將轉換加入至分鏡腳本 helper。

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>參數

*pStoryboard*<br/>
分鏡腳本 COM 物件的指標。

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

以動畫顯示的群組。

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>參數

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會建立內部的分鏡腳本、 建立和套用轉換和排程動畫，如果為 TRUE，否則 bScheduleNow 的資料。 如果 bScheduleNow 為 FALSE 時，您需要呼叫啟動動畫的指定時間的排程。

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

轉換會套用至動畫物件。

```
void ApplyTransitions();
```

### <a name="remarks"></a>備註

這個方法會判斷提示在偵錯模式中如果尚未建立分鏡腳本。 它首先，建立所有的轉換則新增 「 靜態 」 的主要畫面格 （主要畫面格位移而定）、 新增不相依於主要畫面格的轉換、 加入主要畫面格根據轉換和其他主要畫面格，並在上一次將取決於主要畫面格的轉換.

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

建構的動畫群組。

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*pParentController*<br/>
建立群組的動畫控制器指標。

*nGroupID*<br/>
指定 GroupID。

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

建立轉換的 COM 物件的 helper。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>傳回值

此方法成功，否則為 FALSE 則為 TRUE。

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

尋找包含指定的動畫變數的動畫物件。

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>參數

*pVariable*<br/>
動畫變數的指標。

### <a name="return-value"></a>傳回值

動畫的物件，或如果找不到動畫物件為 NULL 指標。

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

會傳回 GroupID。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>傳回值

群組識別碼。

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

指定如何清除從屬於群組的動畫物件的轉換。 如果這個成員為 TRUE 時，轉換會在動畫已排程時自動移除。 否則，您必須手動移除轉換。

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

指定要終結動畫物件的方式。 如果此參數為 TRUE，動畫物件將會自動終結時終結該群組。 否則必須以手動方式終結動畫物件。 預設值為 FALSE。 設定此值設為 TRUE，才是屬於群組的所有動畫物件以動態方式都配置，使用 new 運算子。

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

指定要終結的主要畫面格的方式。 如果此值為 TRUE，會移除所有的主要畫面格，並終結;否則，則會移除從僅限的清單。 預設值為 TRUE。

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

包含一份動畫物件。

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

指向動畫腳本。 只有在動畫上呼叫之後，這個指標是有效。

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

移除，並選擇性地會終結所有主要畫面格屬於群組的動畫。

```
void RemoveKeyframes();
```

### <a name="remarks"></a>備註

如果 m_bAutodestroyKeyframes 成員則為 TRUE，則會移除主要畫面格，並將其終結，否則主要畫面格只會移除從內部清單中的主要畫面格。

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

移除屬於群組的動畫的動畫物件的轉換。

```
void RemoveTransitions();
```

### <a name="remarks"></a>備註

如果 m_bAutoclearTransitions 旗標設為 TRUE 時，這個方法屬於群組的所有動畫物件執行都迴圈，並呼叫 CAnimationObject::ClearTransitions(FALSE)。

##  <a name="schedule"></a>  CAnimationGroup::Schedule

排程在指定時間的動畫。

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>參數

*pTimer*<br/>
動畫計時器指標。

*time*<br/>
指定排程動畫的時間。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE。FALSE 如果方法失敗，或如果是以動畫顯示尚未呼叫與 bScheduleNow 設為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式可排程於指定時間的動畫。 您必須呼叫 Animate bScheduleNow 先設為 FALSE。

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

指示屬於自動群組的所有動畫物件都終結轉換。

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAutoDestroy*<br/>
指定要終結轉換的方式。

### <a name="remarks"></a>備註

您可以將此值設為 FALSE，只有當您配置堆疊上的轉換。 預設值為 TRUE，因此強烈建議您配置使用新運算子的轉換物件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
