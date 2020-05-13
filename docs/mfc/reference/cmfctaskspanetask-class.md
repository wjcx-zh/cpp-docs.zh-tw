---
title: CMFCTasksPaneTask 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375873"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask 類別

類`CMFCTasksPaneTask`是一個幫助器類,表示任務窗格控件的任務 ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md))。 任務物件表示任務組中的項[(CMFC任務窗格任務組](../../mfc/reference/cmfctaskspanetaskgroup-class.md))。 每個工作可以有命令，當使用者按一下工作與工作名稱左邊的圖示時，Framework 就會執行這個命令。

## <a name="syntax"></a>語法

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC任務窗格任務::CMFC任務窗格任務](#cmfctaskspanetask)|建立及初始化 `CMFCTasksPaneTask` 物件。|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC任務窗格任務::設定ACC資料](#setaccdata)|確定當前任務的輔助功能數據。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC任務窗格任務::m_bAutoDestroyWindow](#m_bautodestroywindow)|確定任務視窗是否自動銷毀。|
|[CMFC任務窗格任務::m_bIsBold](#m_bisbold)|確定框架是否以粗體文本繪製任務標籤。|
|[CMFC任務窗格任務::m_dwUserData](#m_dwuserdata)|包含框架與任務關聯的使用者定義數據。 如果任務沒有關聯的數據,則設置為零。|
|[CMFC任務窗格任務::m_hwndTask](#m_hwndtask)|任務視窗的句柄。|
|[CMFC任務窗格任務::m_nIcon](#m_nicon)|框架顯示在任務旁邊的圖像圖像清單中的索引。|
|[CMFC任務窗格任務::m_nWindowHeight](#m_nwindowheight)|任務視窗的高度。 如果任務沒有任務視窗,則此值為零。|
|[CMFC任務窗格任務::m_pGroup](#m_pgroup)|指向此任務所屬`CMFCTasksPaneTaskGroup`的的指標。|
|[CMFC任務窗格任務::m_rect](#m_rect)|指定任務的邊界矩形。|
|[CMFC任務窗格任務::m_strName](#m_strname)|工作的名稱。|
|[CMFC任務窗格任務::m_uiCommandID](#m_uicommandid)|指定框架在使用者按下任務時執行的命令的命令 ID。 如果此值不是有效的命令 ID,則任務將被視為簡單標籤。|

## <a name="remarks"></a>備註

下圖顯示了包含三個工作的工作列:

![任務組,展開](../../mfc/reference/media/nexttaskgrpexpand.png "展開的工作群組")

> [!NOTE]
> 如果任務沒有有效的命令 ID,則將其視為簡單標籤。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>需求

**標題:** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFC任務窗格任務::CMFC任務窗格任務

建立及初始化 `CMFCTasksPaneTask` 物件。

```
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,
    LPCTSTR lpszName,
    int nIcon,
    UINT uiCommandID,
    DWORD dwUserData = 0,
    HWND hwndTask = NULL,
    BOOL bAutoDestroyWindow = FALSE,
    int nWindowHeight = 0);
```

### <a name="parameters"></a>參數

*p組*<br/>
指定工作的[CMFC 工作窗格工作群組](../../mfc/reference/cmfctaskspanetaskgroup-class.md)。

*lpsz名稱*<br/>
指定工作名稱。

*nIcon*<br/>
在影像清單中指定任務圖像的索引。

*uiCommandID*<br/>
指定按一下工作時執行的命令的命令識別碼。

*dwUserData*<br/>
使用者定義的數據。

*hwndTask*<br/>
指定任務視窗的句柄。

*B 自動載毀視窗*<br/>
如果為 TRUE,則任務視窗將自動銷毀。

*n 視窗高度*<br/>
指定任務視窗的高度。

### <a name="remarks"></a>備註

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFC任務窗格任務::m_bAutoDestroyWindow

確定任務視窗是否自動銷毀。

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>備註

設定為 TRUE 以指定應自動銷毀任務視窗[(CMFC 任務窗格任務:::m_hwndTask](#m_hwndtask));否則,FALSE。

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFC任務窗格任務::m_bIsBold

確定是否以粗體文本繪製任務標籤。

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>備註

將此成員設定為 TRUE 以顯示任務標籤的粗體文本。

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFC任務窗格任務::m_dwUserData

包含與任務關聯的使用者定義的數據。 如果沒有數據與任務關聯,則設置為零。

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>備註

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFC任務窗格任務::m_hwndTask

任務視窗的句柄。

```
HWND m_hwndTask;
```

### <a name="remarks"></a>備註

要新增工作視窗,請致電[CMFC 工作窗格::新增視窗](../../mfc/reference/cmfctaskspane-class.md#addwindow)。

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFC任務窗格任務::m_nIcon

圖像清單中的索引位置,用於標識顯示在指定任務旁邊的圖像。

```
int m_nIcon;
```

### <a name="remarks"></a>備註

映射清單由[CMFC 工作表格設定::設定圖示清單](../../mfc/reference/cmfctaskspane-class.md#seticonslist)。

如果要`m_nIcon`在沒有圖像的情況下顯示任務,則設置為 -1。

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFC任務窗格任務::m_nWindowHeight

任務視窗的高度。 如果任務沒有任務視窗,則此值為零。

```
int m_nWindowHeight;
```

### <a name="remarks"></a>備註

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFC任務窗格任務::m_pGroup

指向此任務所屬的[CMFC 任務PaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)的指標。

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>備註

每個任務都必須有一個父組。 通過調用[CMFC任務窗格::添加組](../../mfc/reference/cmfctaskspane-class.md#addgroup),將組添加到任務窗格中。

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFC任務窗格任務::m_rect

指定任務的邊界矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>備註

繪製工作時,由框架計算此值。

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFC任務窗格任務::m_strName

工作的名稱。

```
CString m_strName;
```

### <a name="remarks"></a>備註

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFC任務窗格任務::m_uiCommandID

指定使用者按一下工作時執行的命令的命令 ID。 如果此值不是有效的命令 ID,則任務將被視為簡單標籤。

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>備註

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFC任務窗格任務::設定ACC資料

確定當前任務的輔助功能數據。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[在]表示當前任務的父視窗。

*資料*<br/>
[出]使用當前任務的輔助`CAccessibilityData`數據填充的類型物件。

### <a name="return-value"></a>傳回值

如果*資料*參數已成功填充當前任務的輔助功能資料,則為 TRUE;否則,FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
