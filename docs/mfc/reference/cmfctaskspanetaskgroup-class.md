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
ms.openlocfilehash: 4c24eba646bede462a5f3cfb85715278cfa7daee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366260"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup 類別

該`CMFCTasksPaneTaskGroup`類是[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控件使用的幫助器類。 屬於類型 `CMFCTasksPaneTaskGroup` 的物件表示「 *工作群組*」(Task Group)。 工作群組是 Framework 顯示在具有摺疊按鈕之不同方塊中的項目清單。 方塊可以有選擇性的標題 (群組名稱)。 如果群組已摺疊，工作清單是不可見的。

## <a name="syntax"></a>語法

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC任務窗格任務組::CMFC任務窗格任務組](#cmfctaskspanetaskgroup)|建構 `CMFCTasksPaneTaskGroup` 物件。|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC任務窗格任務組::設定ACC資料](#setaccdata)|確定當前任務組的輔助功能數據。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC任務窗格任務組::m_bIsBottom](#m_bisbottom)|確定任務組是否與任務窗格控制件的底部對齊。|
|[CMFC任務窗格任務組::m_bIsCollapsed](#m_biscollapsed)|確定任務組是否摺疊。|
|[CMFC任務窗格任務組::m_bIsSpecial](#m_bisspecial)|確定任務組是否*特殊。* 框架以不同顏色顯示特殊標題。|
|[CMFC任務窗格任務組::m_lstTasks](#m_lsttasks)|包含任務的內部清單。|
|[CMFC任務窗格任務組::m_rect](#m_rect)|指定組標題的邊界矩形。|
|[CMFC任務窗格任務組::m_rectGroup](#m_rectgroup)|指定組的邊界矩形。|
|[CMFC任務窗格任務組::m_strName](#m_strname)|指定群組的名稱。|

## <a name="remarks"></a>備註

下圖顯示了展開的工作列:

![任務組,展開](../../mfc/reference/media/nexttaskgrpexpand.png "展開的工作群組")

下圖顯示了折疊的工作列:

![摺疊的工作群組](../../mfc/reference/media/nexttaskgrpcollapse.png "摺疊的工作群組")

下圖顯示沒有標題的工作列:

![沒有標題的工作群組](../../mfc/reference/media/nexttaskgrpnocapt.png "沒有標題的工作群組")

下圖顯示了兩個任務組。 通過將`m_bIsSpecial`標誌設置為 TRUE,將第一個任務組標記為特殊,而第二個任務組不特殊。 請注意第一個工作列的標題如何比第二個工作列暗:

![特殊工作群組](../../mfc/reference/media/nexttaskgrpspecial.png "特殊工作群組")

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>需求

**標題:** afxTasksPane.h

## <a name="cmfctaskspanetaskgroupcmfctaskspanetaskgroup"></a><a name="cmfctaskspanetaskgroup"></a>CMFC任務窗格任務組::CMFC任務窗格任務組

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

*lpsz名稱*<br/>
在組標題中指定群組的名稱。

*bIsBottom*<br/>
指定群組是否與工作窗格控制的底部對齊。

*b 特別*<br/>
指定群組是否指定為*特殊*,因此,組標題是否以不同顏色填充。

*bIs 折疊*<br/>
指定組是否摺疊。

*pPage*<br/>
指定此工作群組所屬的屬性頁。

*hIcon*<br/>
指定在組標題中顯示的圖示。

### <a name="remarks"></a>備註

## <a name="cmfctaskspanetaskgroupm_bisbottom"></a><a name="m_bisbottom"></a>CMFC任務窗格任務組::m_bIsBottom

確定任務組是否與任務窗格控制件的底部對齊。

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>備註

只能將一個組與任務窗格控件的底部對齊。 必須最後添加此任務組。 有關詳細資訊,請參閱[CMFC 任務窗格::新增群組](../../mfc/reference/cmfctaskspane-class.md#addgroup)。

## <a name="cmfctaskspanetaskgroupm_biscollapsed"></a><a name="m_biscollapsed"></a>CMFC任務窗格任務組::m_bIsCollapsed

確定任務組是否摺疊。

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>備註

您可以通過調用[CMFCTasksPane::啟用組摺疊](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)來啟用或禁用在任務窗格上摺疊組的能力。

## <a name="cmfctaskspanetaskgroupm_bisspecial"></a><a name="m_bisspecial"></a>CMFC任務窗格任務組::m_bIsSpecial

確定工作組是否*特殊*,以及是否應以不同顏色識別特殊任務組的標題。

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>備註

如果應用程式使用 Windows XP 可視`m_bIsSpecial`主題,並且為 FALSE,則框架`DrawThemeBackground`將使用EBP_NORMALGROUPBACKGROUND標誌調用。 如果`m_bIsSpecial`為 TRUE,則`DrawThemeBackground`框架 使用EBP_SPECIALGROUPBACKGROUND標誌調用。

## <a name="cmfctaskspanetaskgroupm_lsttasks"></a><a name="m_lsttasks"></a>CMFC任務窗格任務組::m_lstTasks

包含任務的內部清單。

```
CObList m_lstTasks;
```

### <a name="remarks"></a>備註

要填寫此清單,請致電[CMFC 工作窗格::新增工作](../../mfc/reference/cmfctaskspane-class.md#addtask)。

## <a name="cmfctaskspanetaskgroupm_rect"></a><a name="m_rect"></a>CMFC任務窗格任務組::m_rect

指定組標題的邊界矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>備註

此值由框架自動計算。

## <a name="cmfctaskspanetaskgroupm_rectgroup"></a><a name="m_rectgroup"></a>CMFC任務窗格任務組::m_rectGroup

指定組的邊界矩形。

```
CRect m_rectGroup;
```

### <a name="remarks"></a>備註

此值由框架自動計算。

## <a name="cmfctaskspanetaskgroupm_strname"></a><a name="m_strname"></a>CMFC任務窗格任務組::m_strName

指定群組的名稱。

```
CString m_strName;
```

### <a name="remarks"></a>備註

如果此值為空,則不顯示組標題,並且無法摺疊組。

## <a name="cmfctaskspanetaskgroupsetaccdata"></a><a name="setaccdata"></a>CMFC任務窗格任務組::設定ACC資料

確定當前任務組的輔助功能數據。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[在]表示當前任務組的父視窗。

*資料*<br/>
[出]使用當前任務組的`CAccessibilityData`輔助功能數據填充的類型物件。

### <a name="return-value"></a>傳回值

如果*資料*參數已成功填充當前任務組的輔助功能資料,則為 TRUE;否則,FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask 類別](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
