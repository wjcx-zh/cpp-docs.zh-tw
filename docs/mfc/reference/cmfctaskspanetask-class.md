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
ms.openlocfilehash: 7d7f5a87dc005ee67f9ce65f4ad686cb27d007c2
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176545"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask 類別

`CMFCTasksPaneTask`類別是一個 helper 類別，代表工作的工作窗格控制項 ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md))。 工作物件代表的工作群組中的項目 ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md))。 每個工作可以有命令，當使用者按一下工作與工作名稱左邊的圖示時，Framework 就會執行這個命令。

## <a name="syntax"></a>語法

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|建立並初始化`CMFCTasksPaneTask`物件。|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|判斷目前的工作的協助工具資料。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|判斷是否自動終結 [工作] 視窗。|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|判斷 framework 是否會繪製工作標籤，以粗體文字。|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|包含 framework 將與工作相關聯的使用者定義資料。 如果工作沒有任何相關聯的資料，請設定為零。|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|[工作] 視窗控制代碼。|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|架構會顯示工作旁邊之映像的映像清單中的索引。|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|[工作] 視窗的高度。 如果工作不有任何 [工作] 視窗，這個值會是零。|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|指標`CMFCTasksPaneTaskGroup`所屬這項工作。|
|[CMFCTasksPaneTask::m_rect](#m_rect)|指定工作的週框矩形。|
|[CMFCTasksPaneTask::m_strName](#m_strname)|工作的名稱。|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|指定的命令，架構就會在使用者按一下工作時執行的命令識別碼。 如果此值不是有效的命令識別碼，此工作會被視為簡單的標籤。|

## <a name="remarks"></a>備註

下圖顯示包含三個工作的工作群組：

![工作群組中，展開](../../mfc/reference/media/nexttaskgrpexpand.png "展開的工作群組")

> [!NOTE]
> 如果工作沒有有效的命令識別碼，它會被視為簡單的標籤。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>需求

**標頭：** afxTasksPane.h

##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask

建立並初始化`CMFCTasksPaneTask`物件。

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

*pGroup*<br/>
指定[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)所屬工作。

*lpszName*<br/>
指定工作的名稱。

*nIcon*<br/>
影像清單中指定工作的映像的索引。

*uiCommandID*<br/>
指定命令時按一下工作所執行的命令識別碼。

*dwUserData*<br/>
使用者定義的資料。

*hwndTask*<br/>
指定 [工作] 視窗的控制代碼。

*bAutoDestroyWindow*<br/>
如果為 TRUE，[工作] 視窗將會自動終結。

*nWindowHeight*<br/>
指定 [工作] 視窗的高度。

### <a name="remarks"></a>備註

##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow

判斷是否自動終結 [工作] 視窗。

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>備註

設定為 TRUE，以指定 [工作] 視窗 ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) 應該予以終結自動; 否則為 FALSE。

##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold

決定是否要將工作的標籤繪製以粗體文字。

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>備註

這個成員設定為 true 會顯示粗體工作標籤文字。

##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData

包含與工作相關聯的使用者定義資料。 如果沒有資料與工作相關聯，請設定為零。

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>備註

##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask

[工作] 視窗控制代碼。

```
HWND m_hwndTask;
```

### <a name="remarks"></a>備註

若要新增工作 視窗，請呼叫[CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow)。

##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon

識別指定的工作旁邊顯示的映像的映像清單中的索引位置。

```
int m_nIcon;
```

### <a name="remarks"></a>備註

影像清單由設定[CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist)。

設定`m_nIcon`為-1，如果您想要顯示的工作，如果沒有影像。

##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight

[工作] 視窗的高度。 如果工作不有任何 [工作] 視窗，這個值會是零。

```
int m_nWindowHeight;
```

### <a name="remarks"></a>備註

##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup

指標[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)所屬這項工作。

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>備註

每個工作都必須有父群組。 將群組新增至工作窗格的藉由呼叫[cmfctaskspane:: Addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。

##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect

指定工作的週框矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>備註

繪製工作時由架構計算此值。

##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName

工作的名稱。

```
CString m_strName;
```

### <a name="remarks"></a>備註

##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID

指定當使用者按一下工作執行命令的命令識別碼。 如果此值不是有效的命令識別碼，此工作會被視為簡單的標籤。

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>備註

##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData

判斷目前的工作的協助工具資料。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[in]表示目前工作的父視窗。

*data*<br/>
[out]型別的物件`CAccessibilityData`，並填入目前的工作的協助工具資料。

### <a name="return-value"></a>傳回值

則為 TRUE*資料*參數，則已成功填入目前的工作的協助工具資料; 否則為 FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
