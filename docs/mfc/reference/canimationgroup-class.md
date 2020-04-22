---
title: CAnimationGroup 類別
ms.date: 03/27/2019
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
ms.openlocfilehash: 14ac32524436ff46449171ad90599e60f63dff2a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750159"
---
# <a name="canimationgroup-class"></a>CAnimationGroup 類別

實現動畫組,該動畫組結合了動畫情節提要、動畫物件和過渡以定義動畫。

## <a name="syntax"></a>語法

```
class CAnimationGroup;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫組::動畫組](#canimationgroup)|構造動畫組。|
|[動畫群組:*動畫群組](#_dtorcanimationgroup)|解構函式。 在銷毀動畫組時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫組:動畫](#animate)|為組設置動畫。|
|[動畫組::應用轉換](#applytransitions)|將轉換應用於動畫物件。|
|[動畫組::尋找動畫物件](#findanimationobject)|查找包含指定動畫變數的動畫物件。|
|[動畫組::取得群體ID](#getgroupid)|返回組識別。|
|[動畫組::刪除關鍵幀](#removekeyframes)|刪除並選擇性地銷毀屬於動畫組的所有關鍵幀。|
|[動畫群組::刪除轉換](#removetransitions)|從屬於動畫組的動畫物件中刪除過渡。|
|[動畫組::時程表](#schedule)|在指定時間安排動畫。|
|[動畫群組::設定自動銷毀轉換](#setautodestroytransitions)|引導屬於組的所有動畫物件自動銷毀過渡。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫組::添加關鍵幀](#addkeyframes)|向情節提要添加關鍵幀的幫助程式。|
|[動畫群組::新增轉換](#addtransitions)|向情節提要添加過渡的説明程式。|
|[動畫群組::建立轉換](#createtransitions)|建立 COM 轉換物件的説明程式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[動畫組::m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除屬於組的動畫物件的轉換。 如果此成員為 TRUE,則在計畫動畫時會自動刪除過渡。 否則,您需要手動刪除過渡。|
|[動畫組:m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定如何銷毀動畫物件。 如果此參數為 TRUE,則在銷毀組時將自動銷毀動畫物件。 否則,必須手動銷毀動畫物件。 預設值為 FALSE。 僅當屬於組的所有動畫物件都使用運算符 new 動態分配時,才將此值設置為 TRUE。|
|[動畫組:m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定如何銷毀關鍵幀。 如果此值為 TRUE,則刪除並銷毀所有關鍵幀;如果此值為 TRUE,則刪除並銷毀所有關鍵幀。否則,它們僅從清單中刪除。 預設值為 TRUE。|
|[動畫組::m_lstAnimationObjects](#m_lstanimationobjects)|包含動畫物件的清單。|
|[動畫組::m_lstKeyFrames](#m_lstkeyframes)|包含關鍵幀的清單。|
|[動畫組::m_pStoryboard](#m_pstoryboard)|指向動畫情節提要。 此指標僅在在 Animate 上調用後有效。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫組::m_nGroupID](#m_ngroupid)|動畫組的唯一標識符。|
|[動畫組::m_pParentController](#m_pparentcontroller)|指向此組所屬的動畫控制器的指標。|

## <a name="remarks"></a>備註

當您使用 CAnimationController::add 動畫物件添加動畫物件時,動畫組由動畫控制器 (CAnimationController) 自動創建。 動畫組由 GroupID 標識,它通常被視為操作動畫組的參數。 GroupID 取自添加到新動畫組的第一個動畫物件。 在調用 CAnimateController::AnimateGroup 後,將創建一個封裝的動畫情節提要,並且可以通過公共成員m_pStoryboard訪問。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CAnimationGroup`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>動畫群組:*動畫群組

解構函式。 在銷毀動畫組時調用。

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>動畫組::添加關鍵幀

向情節提要添加關鍵幀的幫助程式。

```cpp
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要 COM 物件的指標。

*bAddDeep*<br/>
指定此方法是否應添加到依賴於其他關鍵幀的情節提要關鍵幀。

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>動畫群組::新增轉換

向情節提要添加過渡的説明程式。

```cpp
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要 COM 物件的指標。

*bDependon 關鍵幀*

## <a name="canimationgroupanimate"></a><a name="animate"></a>動畫組:動畫

為組設置動畫。

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>參數

*p經理*<br/>
*pTimer*
*b 計劃現在*

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

此方法創建內部情節提要,創建並應用過渡,並在 b-IsisNow 為 TRUE 時安排動畫。 如果 bTimeisNow 是 FALSE,則需要調用計畫才能在指定時間啟動動畫。

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>動畫組::應用轉換

將轉換應用於動畫物件。

```cpp
void ApplyTransitions();
```

### <a name="remarks"></a>備註

如果尚未創建情節提要,此方法 ASSERTS 處於調試模式。 它首先創建所有過渡,然後添加"靜態"關鍵幀(依賴於偏移的關鍵幀),添加不依賴於關鍵幀的過渡,根據過渡和其他關鍵幀添加關鍵幀,最後添加依賴於關鍵幀的過渡。

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>動畫組::動畫組

構造動畫組。

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>參數

*p 家長控制器*<br/>
指向創建組的動畫控制器的指標。

*n集團ID*<br/>
指定組識別碼。

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>動畫群組::建立轉換

建立 COM 轉換物件的説明程式。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>傳回值

TRUE 是方法成功,否則 FALSE。

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>動畫組::尋找動畫物件

查找包含指定動畫變數的動畫物件。

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>參數

*pvariable*<br/>
指向動畫變數的指標。

### <a name="return-value"></a>傳回值

指向動畫物件的指標,如果未找到動畫物件,則為 NULL。

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>動畫組::取得群體ID

返回組識別。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>傳回值

組標識碼。

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>動畫組::m_bAutoclearTransitions

指定如何清除屬於組的動畫物件的轉換。 如果此成員為 TRUE,則在計畫動畫時會自動刪除過渡。 否則,您需要手動刪除過渡。

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>動畫組:m_bAutodestroyAnimationObjects

指定如何銷毀動畫物件。 如果此參數為 TRUE,則在銷毀組時將自動銷毀動畫物件。 否則,必須手動銷毀動畫物件。 預設值為 FALSE。 僅當屬於組的所有動畫物件都使用運算符 new 動態分配時,才將此值設置為 TRUE。

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>動畫組:m_bAutodestroyKeyframes

指定如何銷毀關鍵幀。 如果此值為 TRUE,則刪除並銷毀所有關鍵幀;如果此值為 TRUE,則刪除並銷毀所有關鍵幀。否則,它們僅從清單中刪除。 預設值為 TRUE。

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>動畫組::m_lstAnimationObjects

包含動畫物件的清單。

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>動畫組::m_lstKeyFrames

包含關鍵幀的清單。

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>動畫組::m_nGroupID

動畫組的唯一標識符。

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>動畫組::m_pParentController

指向此組所屬的動畫控制器的指標。

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>動畫組::m_pStoryboard

指向動畫情節提要。 此指標僅在在 Animate 上調用後有效。

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>動畫組::刪除關鍵幀

刪除並選擇性地銷毀屬於動畫組的所有關鍵幀。

```cpp
void RemoveKeyframes();
```

### <a name="remarks"></a>備註

如果m_bAutodestroyKeyframes成員為 TRUE,則關鍵幀將被刪除並銷毀,否則關鍵幀將僅從關鍵幀的內部清單中刪除。

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>動畫群組::刪除轉換

從屬於動畫組的動畫物件中刪除過渡。

```cpp
void RemoveTransitions();
```

### <a name="remarks"></a>備註

如果m_bAutoclearTransitions標誌設置為 TRUE,則此方法將迴圈訪問屬於該組的所有動畫物件,並調用 CAnimationObject:::清除轉換(FALSE)。

## <a name="canimationgroupschedule"></a><a name="schedule"></a>動畫組::時程表

在指定時間安排動畫。

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>參數

*pTimer*<br/>
指向動畫計時器的指標。

*time*<br/>
指定計劃動畫的時間。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;如果方法失敗或 Animate 尚未調用,則使用 b-計劃現在設置為 FALSE,則 FALSE。

### <a name="remarks"></a>備註

調用此函數以在指定時間安排動畫。 您必須先將 b-計劃現在設定為 FALSE 的 Animate。

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>動畫群組::設定自動銷毀轉換

引導屬於組的所有動畫物件自動銷毀過渡。

```cpp
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAuto銷毀*<br/>
指定如何銷毀轉換。

### <a name="remarks"></a>備註

僅當在堆疊上分配過渡時,才將此值設置為 FALSE。 預設值為 TRUE,因此強烈建議使用運算符 new 分配過渡物件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
