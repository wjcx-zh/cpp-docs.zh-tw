---
title: CCoNtextMenuManager 類別
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78868986"
---
# <a name="ccontextmenumanager-class"></a>CCoNtextMenuManager 類別

`CContextMenuManager` 物件會管理快捷方式功能表，也稱為內容功能表。

## <a name="syntax"></a>語法

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCoNtextMenuManager::CCoNtextMenuManager](#ccontextmenumanager)|建構 `CContextMenuManager` 物件。|
|`CContextMenuManager::~CContextMenuManager`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCoNtextMenuManager：： AddMenu](#addmenu)|加入新的快捷方式功能表。|
|[CCoNtextMenuManager::GetMenuById](#getmenubyid)|傳回與所提供資源識別碼相關聯之功能表的控制碼。|
|[CCoNtextMenuManager::GetMenuByName](#getmenubyname)|傳回符合提供的功能表名稱之功能表的控制碼。|
|[CCoNtextMenuManager::GetMenuNames](#getmenunames)|傳回功能表名稱的清單。|
|[CCoNtextMenuManager：： LoadState](#loadstate)|載入儲存在 Windows 登錄中的快捷方式功能表。|
|[CCoNtextMenuManager：： ResetState](#resetstate)|從內容功能表管理員清除快捷方式功能表。|
|[CCoNtextMenuManager：： SaveState](#savestate)|將快捷方式功能表儲存至 Windows 登錄。|
|[CCoNtextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|控制當顯示新的快捷方式功能表時，`CContextMenuManager` 是否關閉使用中的快捷方式功能表。|
|[CCoNtextMenuManager::ShowPopupMenu](#showpopupmenu)|顯示指定的快捷方式功能表。|
|[CCoNtextMenuManager：： Trackpopupmenu 讓](#trackpopupmenu)|顯示指定的快捷方式功能表。 傳回所選功能表命令的索引。|

## <a name="remarks"></a>備註

`CContextMenuManager` 管理快捷方式功能表，並確保它們具有一致的外觀。

您不應該手動建立 `CContextMenuManager` 物件。 應用程式的架構會建立 `CContextMenuManager` 物件。 不過，當您的應用程式初始化時，您應該呼叫[CWinAppEx：： InitCoNtextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 。 在初始化內容管理員之後，請使用[CWinAppEx：： GetCoNtextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)方法來取得應用程式內容管理員的指標。

您可以藉由呼叫 `AddMenu`，在執行時間建立快捷方式功能表。 如果您想要顯示功能表，而不先收到使用者輸入，請呼叫 `ShowPopupMenu`。 當您想要建立功能表並等候使用者輸入時，會使用 `TrackPopupMenu`。 `TrackPopupMenu` 會傳回所選命令的索引，如果使用者結束但未選取任何專案，則傳回0。

`CContextMenuManager` 也可以將其狀態儲存並載入至 Windows 登錄。

## <a name="example"></a>範例

下列範例示範如何將功能表加入至 `CContextMenuManager` 物件，以及當 `CContextMenuManager` 物件顯示新的快顯功能表時，如何關閉現用快顯功能表。 此程式碼片段是[自訂頁面範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>需求

**標頭：** afxcoNtextmenumanager。h

##  <a name="addmenu"></a>CCoNtextMenuManager：： AddMenu

將新的快捷方式功能表加入至[CCoNtextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>參數

*uiMenuNameResId*<br/>
在包含新功能表名稱的字串資源識別碼。

*uiMenuResId*<br/>
在功能表資源識別碼。

*lpszName*<br/>
在包含新功能表名稱的字串。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;如果方法失敗，則為0。

### <a name="remarks"></a>備註

如果*uiMenuResId*無效，或 `CContextMenuManager`中已經有另一個同名的功能表，這個方法就會失敗。

##  <a name="ccontextmenumanager"></a>CCoNtextMenuManager::CCoNtextMenuManager

結構[CCoNtextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。

```
CContextMenuManager();
```

### <a name="remarks"></a>備註

在大部分的情況下，您不應該手動建立 `CContextMenuManager`。 應用程式的架構會建立 `CContextMenuManager` 物件。 在初始化應用程式期間，您應該呼叫[CWinAppEx：： InitCoNtextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 。 若要取得內容管理員的指標，請呼叫[CWinAppEx：： GetCoNtextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。

##  <a name="getmenubyid"></a>CCoNtextMenuManager::GetMenuById

傳回與指定資源識別碼相關聯之功能表的控制碼。

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>參數

*nMenuResId*<br/>
在功能表的資源識別碼。

### <a name="return-value"></a>傳回值

如果找不到功能表，則為相關聯功能表或 `NULL` 的控制碼。

##  <a name="getmenubyname"></a>CCoNtextMenuManager::GetMenuByName

傳回特定功能表的控制碼。

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>參數

*lpszName*<br/>
在包含要抓取之功能表名稱的字串。

*puiOrigResID*<br/>
脫銷UINT 的指標。 如果找到，此參數會包含指定功能表的資源識別碼。

### <a name="return-value"></a>傳回值

符合*lpszName*所指定之名稱的功能表控制碼。 如果沒有名為*lpszName*的功能表，則為 Null。

### <a name="remarks"></a>備註

如果此方法找到符合*lpszName*的功能表，`GetMenuByName` 會將功能表資源識別碼儲存在參數*puiOrigResID*中。

##  <a name="getmenunames"></a>CCoNtextMenuManager::GetMenuNames

傳回已新增至[CCoNtextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)的功能表名稱清單。

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>參數

*listOfNames*<br/>
脫銷[CStringList](../../mfc/reference/cstringlist-class.md)參數的參考。 這個方法會將功能表名稱的清單寫入此參數。

##  <a name="loadstate"></a>CCoNtextMenuManager：： LoadState

從 Windows 登錄載入與[CCoNtextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)相關聯的資訊。

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在包含登錄機碼之相對路徑的字串。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

*LpszProfileName*參數不是登錄專案的絕對路徑。 它是新增至您應用程式的預設登錄機碼結尾的相對路徑。 若要取得或設定預設的登錄機碼，請分別使用[CWinAppEx：： GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx：： SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)方法。

使用方法[CCoNtextMenuManager：： SaveState](#savestate) ，將快捷方式功能表儲存至登錄。

##  <a name="resetstate"></a>CCoNtextMenuManager：： ResetState

從與[CCoNtextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)相關聯的快捷方式功能表清除所有專案。

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;如果發生失敗，則為 FALSE。

### <a name="remarks"></a>備註

這個方法會清除快顯功能表，並將其從 `CContextMenuManager`中移除。

##  <a name="savestate"></a>CCoNtextMenuManager：： SaveState

將與[CCoNtextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)相關聯的資訊儲存至 Windows 登錄。

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在包含登錄機碼之相對路徑的字串。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

*LpszProfileName*參數不是登錄專案的絕對路徑。 它是新增至您應用程式的預設登錄機碼結尾的相對路徑。 若要取得或設定預設的登錄機碼，請分別使用[CWinAppEx：： GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx：： SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)方法。

使用方法[CCoNtextMenuManager：： LoadState](#loadstate)從登錄載入快捷方式功能表。

##  <a name="setdontcloseactivemenu"></a>CCoNtextMenuManager::SetDontCloseActiveMenu

控制當[CCoNtextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)顯示新的快顯功能表時，是否關閉作用中的快顯功能表。

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
在布林值參數，控制是否要關閉現用快顯功能表。 值為 TRUE 時，表示未關閉作用中的快顯功能表。 FALSE 表示已關閉現用快顯功能表。

### <a name="remarks"></a>備註

根據預設，`CContextMenuManager` 會關閉作用中的快顯功能表。

##  <a name="showpopupmenu"></a>CCoNtextMenuManager::ShowPopupMenu

顯示指定的快捷方式功能表。

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>參數

*uiMenuResId*<br/>
在這個方法將會顯示之功能表的資源識別碼。

*x*<br/>
在在用戶端座標中，快捷方式功能表的水準位移。

*y*<br/>
在在用戶端座標中，快捷方式功能表的垂直位移

*pWndOwner*<br/>
在快捷方式功能表父視窗的指標。

*bOwnMessage*<br/>
在布林值參數，指出訊息的路由方式。 如果*bOwnMessage*為 FALSE，則會使用標準 MFC 路由。 否則， *pWndOwner*會接收訊息。

*hmenuPopup*<br/>
在這個方法將會顯示之功能表的控制碼。

*bAutoDestroy*<br/>
在布林值參數，指出是否會自動終結功能表。

*bRightAlign*<br/>
在布林值參數，指出功能表項目的對齊方式。 如果*bRightAlign*為 TRUE，則功能表靠右到左的讀取順序為右對齊。

### <a name="return-value"></a>傳回值

如果方法成功顯示功能表，第一個方法多載會傳回非零;否則為0。 如果快捷方式功能表正確顯示，第二個方法多載會傳回[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)的指標;否則為 Null。

### <a name="remarks"></a>備註

這個方法類似于[CCoNtextMenuManager：： trackpopupmenu 讓](#trackpopupmenu)方法，因為這兩種方法都會顯示快捷方式功能表。 不過，`TrackPopupMenu` 會傳回所選功能表命令的索引。

如果參數*bAutoDestroy*為 FALSE，您就必須手動呼叫繼承的 `DestroyMenu` 方法來釋放記憶體資源。 `ShowPopupMenu` 的預設執行不會使用*bAutoDestroy*參數。 它會提供供日後使用，或用於從 `CContextMenuManager` 類別衍生的自訂類別。

##  <a name="trackpopupmenu"></a>CCoNtextMenuManager：： Trackpopupmenu 讓

顯示指定的快捷方式功能表，並傳回所選快捷方式功能表命令的索引。

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>參數

*hmenuPopup*<br/>
在這個方法所顯示之快捷方式功能表的控制碼。

*x*<br/>
在在用戶端座標中，快捷方式功能表的水準位移。

*y*<br/>
在在用戶端座標中，快捷方式功能表的垂直位移。

*pWndOwner*<br/>
在快捷方式功能表父視窗的指標。

*bRightAlign*<br/>
在布林值參數，指出功能表項目的對齊方式。 如果*bRightAlign*為 TRUE，則功能表靠右到左的讀取順序為右對齊。 如果*bRightAlign*為 FALSE，則會從左至右的讀取順序，將功能表靠左對齊。

### <a name="return-value"></a>傳回值

使用者選擇之命令的功能表命令識別碼;如果使用者關閉快捷方式功能表而不選取功能表命令，則為0。

### <a name="remarks"></a>備註

這個方法會當做模式呼叫來顯示快捷方式功能表。 在使用者關閉快捷方式功能表或選取命令之前，應用程式將不會繼續執行程式碼中的下面這一行。 您可以用來顯示快捷方式功能表的替代方法是[CCoNtextMenuManager：： ShowPopupMenu](#showpopupmenu)。 該方法不是強制回應的呼叫，而且不會傳回所選命令的識別碼。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
