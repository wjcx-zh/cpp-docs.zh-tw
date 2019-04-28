---
title: CMFCTasksPaneTaskGroup 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: a28f00fb732727ec1334946a9e752679307cd3a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222218"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup 類別

`CMFCTasksPaneTaskGroup`類別是所使用的 helper 類別[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控制項。 屬於類型 `CMFCTasksPaneTaskGroup` 的物件表示「 *工作群組*」(Task Group)。 工作群組是 Framework 顯示在具有摺疊按鈕之不同方塊中的項目清單。 方塊可以有選擇性的標題 (群組名稱)。 如果群組已摺疊，工作清單是不可見的。

## <a name="syntax"></a>語法

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|建構 `CMFCTasksPaneTaskGroup` 物件。|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|判斷目前的工作群組的協助工具資料。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|決定是否要將工作群組對齊工作窗格控制項的底部。|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|決定是否要摺疊工作群組。|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|判斷是否要為工作群組*特殊。* 架構會顯示特殊的標題中不同的色彩。|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|包含內部工作清單。|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|指定群組標題的週框矩形。|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|指定群組的週框矩形。|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|指定群組的名稱。|

## <a name="remarks"></a>備註

下圖顯示已展開的工作群組：

![工作群組中，展開](../../mfc/reference/media/nexttaskgrpexpand.png "展開的工作群組")

下圖顯示已摺疊的工作群組：

![摺疊工作群組](../../mfc/reference/media/nexttaskgrpcollapse.png "摺疊工作群組")

下圖顯示沒有標題的工作群組：

![沒有標題的工作群組](../../mfc/reference/media/nexttaskgrpnocapt.png "沒有標題的工作群組")

下圖顯示兩個工作群組。 第一個工作群組設定標示為特殊`m_bIsSpecial`旗標設為 TRUE，而第二個工作群組並不特殊。 請注意如何在第一個工作群組的標題比第二個工作群組深：

![特殊的工作群組](../../mfc/reference/media/nexttaskgrpspecial.png "特殊工作群組")

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>需求

**標頭：** afxTasksPane.h

##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

建構 `CMFCTasksPaneTaskGroup` 物件。

```
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,
    BOOL bIsBottom,
    BOOL bIsSpecial=FALSE,
    BOOL bIsCollapsed=FALSE,
    CMFCTasksPanePropertyPage* pPage=NULL,
    HICON hIcon=NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
群組標題中指定的群組名稱。

*bIsBottom*<br/>
指定群組是否工作窗格控制項的底部對齊。

*bIsSpecial*<br/>
指定是否要將群組指定為*特殊*，因此，不論群組標題填滿不同色彩。

*bIsCollapsed*<br/>
指定是否要摺疊的群組。

*pPage*<br/>
指定此工作群組所屬的屬性頁。

*hIcon*<br/>
指定在群組標題中顯示的圖示。

### <a name="remarks"></a>備註

##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom

決定是否要將工作群組對齊工作窗格控制項的底部。

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>備註

只有一個群組可以工作窗格控制項的底部對齊。 此工作群組必須新增上一次。 如需詳細資訊，請參閱 < [cmfctaskspane:: Addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。

##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed

決定是否要摺疊工作群組。

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>備註

您可以啟用或停用的功能，在 [工作] 窗格上摺疊群組，藉由呼叫[cmfctaskspane:: Enablegroupcollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)。

##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial

判斷是否要為工作群組*特殊*和特殊工作群組的標題是否應該由不同的色彩。

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>備註

如果您的應用程式使用 Windows XP 的視覺效果佈景主題及`m_bIsSpecial`為 FALSE 時，這個架構會呼叫`DrawThemeBackground`EBP_NORMALGROUPBACKGROUND 旗標。 如果`m_bIsSpecial`為 TRUE 時，這個架構會呼叫`DrawThemeBackground`EBP_SPECIALGROUPBACKGROUND 旗標。

##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks

包含內部工作清單。

```
CObList m_lstTasks;
```

### <a name="remarks"></a>備註

若要填滿這份清單，請呼叫[cmfctaskspane:: Addtask](../../mfc/reference/cmfctaskspane-class.md#addtask)。

##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect

指定群組標題的週框矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>備註

由架構自動計算此值。

##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup

指定群組的週框矩形。

```
CRect m_rectGroup;
```

### <a name="remarks"></a>備註

由架構自動計算此值。

##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName

指定群組的名稱。

```
CString m_strName;
```

### <a name="remarks"></a>備註

如果這個值是空的不會顯示群組標題，並不能摺疊的群組。

##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData

判斷目前的工作群組的協助工具資料。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[in]表示目前的工作群組的父視窗。

*data*<br/>
[out]型別的物件`CAccessibilityData`，並填入目前的工作群組的協助工具資料。

### <a name="return-value"></a>傳回值

則為 TRUE*資料*參數，則已成功填入目前的工作群組的協助工具資料; 否則為 FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask 類別](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
