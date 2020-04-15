---
title: CJumpList 類別
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 98d6bec3d33c9060ebb741111dff793f64cc7cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372326"
---
# <a name="cjumplist-class"></a>CJumpList 類別

A`CJumpList`是右鍵按一下工作列中的圖示時顯示的快捷方式清單。

## <a name="syntax"></a>語法

```
class CJumpList;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[跳轉清單::跳轉清單](#cjumplist)|建構 `CJumpList` 物件。|
|[跳轉清單:*跳轉清單](#_dtorcjumplist)|終結 `CJumpList` 物件。|

|名稱|描述|
|----------|-----------------|
|[跳轉清單::中止清單](#abortlist)|在不提交的情況下中止清單生成事務。|
|[跳轉清單::新增目的地](#adddestination)|已多載。 將目標添加到清單中。|
|[跳轉清單::新增已知類別](#addknowncategory)|將已知類別追加到清單中。|
|[跳轉清單::新增工作](#addtask)|已多載。 將項添加到規範任務類別。|
|[跳轉清單::新增工作](#addtasks)|將項添加到規範任務類別。|
|[跳轉清單::新增工作分離器](#addtaskseparator)|在任務之間添加分隔符。|
|[跳轉清單:清除所有](#clearall)|刪除到目前為止已添加到當前實例`CJumpList`的所有任務和目標。|
|[跳轉清單:清除所有目標](#clearalldestinations)|刪除到目前為止已添加到當前實例`CJumpList`的所有目標。|
|[跳轉清單:提交清單](#commitlist)|結束清單生成事務並將報告的清單提交到關聯的存儲(在這種情況下為註冊表)。|
|[跳轉清單:抓取目的地清單](#getdestinationlist)|檢索指向目標清單的介面指標。|
|[跳轉清單:取得 MaxSlots](#getmaxslots)|檢索最大項目數,包括可在調用應用程式的目標功能表中顯示的類別標頭。|
|[跳轉清單::抓取刪除的項目](#getremoveditems)|返回表示已刪除目標的項陣列。|
|[跳轉清單::初始化清單](#initializelist)|開始清單生成事務。|
|[跳轉清單::設定AppID](#setappid)|為要生成的清單設置應用程式使用者模型 ID。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>需求

**標題:** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>跳轉清單:*跳轉清單

終結 `CJumpList` 物件。

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>跳轉清單::中止清單

在不提交的情況下中止清單生成事務。

```
void AbortList();
```

### <a name="remarks"></a>備註

調用此方法的效果與不調用`CJumpList``CommitList`銷毀的效果相同。

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>跳轉清單::新增目的地

將目標添加到清單中。

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>參數

*lpcsz 類別名稱*<br/>
指定類別名稱。 如果指定的類別不存在,將創建該類別。

*序列路徑*<br/>
指定目標檔的路徑。

*序列名稱*<br/>
指定類別名稱。 如果指定的類別不存在,將創建該類別。

*p殼牌項目*<br/>
指定表示要添加目標的行殼專案。

*p殼牌連結*<br/>
指定表示要添加目標的 Shell 連結。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

內部實例`CJumpList`累積添加的目標,然後在`CommitList`中提交它們。

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>跳轉清單::新增已知類別

將已知類別追加到清單中。

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>參數

*類別*<br/>
指定已知的類別類型。 可以是KDC_RECENT,也可以是KDC_KNOWN。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

已知類別是我們將自動計算每個使用的應用程式的頻繁和最近類別`SHAddToRecentDocs`(或在某些情況下間接使用它,因為 shell 會代表應用程式調用它)。

## <a name="cjumplistaddtask"></a><a name="addtask"></a>跳轉清單::新增工作

將項添加到規範任務類別。

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>參數

*str 目標執行路徑*<br/>
指定目標任務路徑。

*斯特魯茨線*<br/>
指定*strTarget 可執行路徑*指定的執行檔的命令列參數。

*斯特標題*<br/>
將在目標清單中顯示的任務名稱。

*序列圖示位置*<br/>
將在「目標清單」中以及標題中顯示的圖示的位置。

*iIconIndex*<br/>
圖示索引。

*p殼牌連結*<br/>
表示要添加的任務的 Shell 連結。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

實例`CJumpList`將累積指定的任務,並在`CommitList`期間將它們添加到目標清單。 任務項將顯示在應用程式目標功能表底部的類別中。 此類別在 UI 中填充時優先於所有其他類別。

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>跳轉清單::新增工作

將項添加到規範任務類別。

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>參數

*pObject集合*<br/>
要添加的任務的集合。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

CJumpList 的實例累積指定的任務,並在`CommitList`期間將它們添加到目標清單中。 任務項將顯示在應用程式目標功能表底部的類別中。 此類別在 UI 中填充時優先於所有其他類別。

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>跳轉清單::新增工作分離器

在任務之間添加分隔符。

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>傳回值

如果成功,則非零,如果為非零,則為 0。

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>跳轉清單::跳轉清單

建構 `CJumpList` 物件。

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>參數

*bAuto 提交*<br/>
如果此參數為 FALSE,則清單不會自動提交到析構函數中。

## <a name="cjumplistclearall"></a><a name="clearall"></a>跳轉清單:清除所有

刪除到目前為止已添加到當前實例`CJumpList`的所有任務和目標。

```
void ClearAll();
```

### <a name="remarks"></a>備註

此方法清除和釋放所有數據和內部介面。

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>跳轉清單:清除所有目標

刪除到目前為止已添加到 CJumpList 當前實例的所有目標。

```
void ClearAllDestinations();
```

### <a name="remarks"></a>備註

如果需要刪除到目前為止在目標清單生成會話中添加的所有目標,然後再次添加其他目標,請調用此功能。 如果內部`ICustomDestinationList`已初始化,則它保持活動狀態。

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>跳轉清單:提交清單

結束清單生成事務並將報告的清單提交到關聯的存儲(本例中的註冊表)。

```
BOOL CommitList();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

提交是原子的。 如果提交失敗,將返回錯誤。  呼叫`CommitList`時,將清理目前已刪除項的清單。 呼叫此方法將重置物件,使其沒有活動的列表生成事務。 要更新清單,`BeginList`需要再次呼叫。

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>跳轉清單:抓取目的地清單

檢索指向目標清單的介面指標。

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

如果跳轉清單尚未初始化,或已提交或中止,則返回的值將為 NULL。

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>跳轉清單:取得 MaxSlots

檢索最大項目數,包括可在調用應用程式的目標功能表中顯示的類別標頭。

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

應用程式只能報告多個項和類別標頭,這些項目和類別標頭組合到此值。 如果調用`AppendCategory``AppendKnownCategory`、`AddUserTasks`或 超過此號碼,它們將返回失敗。

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>跳轉清單::抓取刪除的項目

返回表示已刪除目標的項陣列。

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

在跳轉清單的初始化過程中檢索已刪除的目標。 生成新目標清單時,應用程式應首先處理刪除的目標清單,清除其跟蹤數據,以訪問刪除的清單枚舉器返回的任何項。 如果應用程式嘗試提供當前調用啟動`BeginList`的事務中剛剛刪除的項,則重新添加該項的方法調用將失敗,以確保應用程式遵守已刪除的清單。

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>跳轉清單::初始化清單

開始清單生成事務。

```
BOOL InitializeList();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

不需要顯示式呼叫此方法,除非您希望檢索`ICustomDestinationList`指向的指標,`GetDestinationList`使用`GetMaxSlots`的可用插槽數或使用`GetRemovedItems`或使用的已刪除項清單。

## <a name="cjumplistsetappid"></a><a name="setappid"></a>跳轉清單::設定AppID

為要生成的清單設置應用程式使用者模型 ID。

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>參數

*斯特雷帕維德*<br/>
指定應用程式使用者模型 ID 的字串。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
