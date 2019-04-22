---
title: CContextMenuManager 類別
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
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779790"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 類別

`CContextMenuManager`物件管理捷徑功能表，也稱為操作功能表。

## <a name="syntax"></a>語法

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|建構 `CContextMenuManager` 物件。|
|`CContextMenuManager::~CContextMenuManager`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CContextMenuManager::AddMenu](#addmenu)|加入新的快顯功能表。|
|[CContextMenuManager::GetMenuById](#getmenubyid)|傳回與提供的資源識別碼相關聯的功能表的控制代碼|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|傳回符合所提供的功能表名稱的功能表的控制代碼。|
|[CContextMenuManager::GetMenuNames](#getmenunames)|傳回一份功能表名稱。|
|[CContextMenuManager::LoadState](#loadstate)|載入儲存在 Windows 登錄中的捷徑功能表。|
|[CContextMenuManager::ResetState](#resetstate)|清除的快顯功能表，從操作功能表管理員。|
|[CContextMenuManager::SaveState](#savestate)|將 Windows 登錄中的捷徑功能表。|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|控制項是否`CContextMenuManager`時它會顯示新的快顯功能表關閉使用中的快顯功能表。|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|顯示指定的快顯功能表。|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|顯示指定的快顯功能表。 傳回選取之功能表命令的索引。|

## <a name="remarks"></a>備註

`CContextMenuManager` 管理捷徑功能表，並確定它們有一致的外觀。

您不應建立`CContextMenuManager`手動物件。 您的應用程式的架構會建立`CContextMenuManager`物件。 不過，您應該呼叫[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)初始化您的應用程式的時間。 在初始化 「 內容管理員 」 之後, 使用的方法[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)來取得您的應用程式的內容管理員的指標。

您可以在執行階段建立捷徑功能表，藉由呼叫`AddMenu`。 如果您想要顯示的功能表，第一個接收使用者輸入的情況下，呼叫`ShowPopupMenu`。 `TrackPopupMenu` 當您想要建立功能表，並等候使用者輸入時，會使用。 `TrackPopupMenu` 傳回選取的命令或 0 的索引; 如果使用者已結束但不選取任何項目。

`CContextMenuManager`也可以儲存及載入 Windows 登錄其狀態。

## <a name="example"></a>範例

下列範例示範如何加入至功能表`CContextMenuManager`物件，以及如何不關閉使用中的快顯功能表時`CContextMenuManager`物件會顯示新的快顯功能表。 此程式碼片段是一部分[自訂頁面範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>需求

**標頭：** afxcontextmenumanager.h

##  <a name="addmenu"></a>  CContextMenuManager::AddMenu

加入新的快顯功能表來[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。

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
[in]包含新的功能表名稱的字串資源識別碼。

*uiMenuResId*<br/>
[in]功能表資源識別碼。

*lpszName*<br/>
[in]包含新的功能表名稱的字串。

### <a name="return-value"></a>傳回值

如果方法成功，為非零0，表示方法將會失敗。

### <a name="remarks"></a>備註

如果這個方法會失敗*uiMenuResId*無效，或如果具有相同名稱的另一個功能表中已`CContextMenuManager`。

##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager

建構[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。

```
CContextMenuManager();
```

### <a name="remarks"></a>備註

在大部分情況下，您不應建立`CContextMenuManager`以手動方式。 您的應用程式的架構會建立`CContextMenuManager`物件。 您應該呼叫[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)您的應用程式初始化期間。 若要取得內容管理員的指標，呼叫[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。

##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById

傳回與指定的資源識別碼相關聯的功能表的控制代碼

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>參數

*nMenuResId*<br/>
[in]功能表資源識別碼。

### <a name="return-value"></a>傳回值

相關聯的功能表的控制代碼或`NULL`如果找不到功能表。

##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName

傳回特定的功能表的控制代碼。

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>參數

*lpszName*<br/>
[in]字串，包含要擷取功能表的名稱。

*puiOrigResID*<br/>
[out]UINT 指標。 這個參數會包含指定的功能表中，資源識別碼，如果找到。

### <a name="return-value"></a>傳回值

所指定的名稱相符的功能表的控制代碼*lpszName*。 如果沒有呼叫功能表則為 NULL *lpszName*。

### <a name="remarks"></a>備註

如果這個方法會尋找符合的功能表*lpszName*，`GetMenuByName`參數中儲存功能表資源識別碼*puiOrigResID*。

##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames

傳回已加入的功能表名稱的清單[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>參數

*listOfNames*<br/>
[out]參考[CStringList](../../mfc/reference/cstringlist-class.md)參數。 這個方法會寫入此參數中的功能表名稱的清單。

##  <a name="loadstate"></a>  CContextMenuManager::LoadState

載入資訊與相關聯[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)從 Windows 登錄。

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]字串，包含相對路徑的登錄機碼。

### <a name="return-value"></a>傳回值

如果方法成功則為非零否則為 0。

### <a name="remarks"></a>備註

*LpszProfileName*參數不是絕對路徑的登錄項目。 它是相對路徑新增至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)並[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分別。

使用方法[CContextMenuManager::SaveState](#savestate)登錄中儲存的快顯功能表。

##  <a name="resetstate"></a>  CContextMenuManager::ResetState

清除所有項目相關聯的快顯功能表[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)。

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE如果發生失敗，則為 FALSE。

### <a name="remarks"></a>備註

這個方法會清除快顯功能表，並將它們從移除`CContextMenuManager`。

##  <a name="savestate"></a>  CContextMenuManager::SaveState

儲存資訊與相關聯[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)至 Windows 登錄。

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]字串，包含相對路徑的登錄機碼。

### <a name="return-value"></a>傳回值

如果方法成功則為非零否則為 0。

### <a name="remarks"></a>備註

*LpszProfileName*參數不是絕對路徑的登錄項目。 它是相對路徑新增至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設登錄機碼，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)並[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分別。

使用方法[CContextMenuManager::LoadState](#loadstate)從登錄載入的快顯功能表。

##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu

控制項是否[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)時它會顯示新的快顯功能表關閉使用中的快顯功能表。

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
[in]布林值參數可控制是否要關閉使用中的快顯功能表。 如果為 true 值表示不會關閉使用中的快顯功能表。 FALSE 表示作用中的快顯功能表已關閉。

### <a name="remarks"></a>備註

根據預設，`CContextMenuManager`關閉使用中的快顯功能表。

##  <a name="showpopupmenu"></a>  CContextMenuManager::ShowPopupMenu

顯示指定的快顯功能表。

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
[in]這個方法會顯示的功能表資源識別碼。

*x*<br/>
[in]在水平位移的工作區座標中的捷徑功能表時。

*y*<br/>
[in]捷徑功能表，在工作區座標的垂直位移

*pWndOwner*<br/>
[in]快顯功能表的父視窗指標。

*bOwnMessage*<br/>
[in]表示訊息會路由傳送的布林參數。 如果*bOwnMessage*是 FALSE，標準的 MFC 路由使用。 否則，請*pWndOwner*接收訊息。

*hmenuPopup*<br/>
[in]這個方法會顯示功能表的控制代碼。

*bAutoDestroy*<br/>
[in]布林值參數，指出功能表是否將會自動終結。

*bRightAlign*<br/>
[in]布林值參數，指出功能表項目對齊的方式。 如果*bRightAlign*為 TRUE，功能表會靠右對齊的由右至左讀取順序。

### <a name="return-value"></a>傳回值

第一個方法多載會傳回非零值，如果方法成功; 顯示的功能表否則為 0。 第二個方法多載會傳回的指標[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)如果快顯功能表會顯示; 否則為 NULL。

### <a name="remarks"></a>備註

這個方法類似於方法[CContextMenuManager::TrackPopupMenu](#trackpopupmenu) ，因為這兩種方法會顯示快顯功能表。 不過，`TrackPopupMenu`傳回選取之功能表命令的索引。

如果參數*bAutoDestroy*為 FALSE 時，您必須以手動方式呼叫繼承`DestroyMenu`方法，以釋放記憶體資源。 預設實作`ShowPopupMenu`不使用參數*bAutoDestroy*。 它可供未來使用或自訂的類別衍生自`CContextMenuManager`類別。

##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu

顯示指定的捷徑功能表，並傳回所選的捷徑功能表命令的索引。

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
[in]這個方法會顯示快顯功能表的控制代碼。

*x*<br/>
[in]在水平位移的工作區座標中的捷徑功能表時。

*y*<br/>
[in]垂直的捷徑功能表，在工作區座標的位移。

*pWndOwner*<br/>
[in]快顯功能表的父視窗指標。

*bRightAlign*<br/>
[in]布林值參數，指出功能表項目對齊的方式。 如果*bRightAlign*為 TRUE，功能表會靠右對齊的由右至左讀取順序。 如果*bRightAlign*為 FALSE 時，功能表是靠左對齊，由左到右的讀取順序。

### <a name="return-value"></a>傳回值

使用者選擇; 命令的功能表命令識別碼0，表示使用者關閉快顯功能表，而不選取功能表命令。

### <a name="remarks"></a>備註

此方法做為強制回應的呼叫，來顯示快顯功能表。 應用程式不會為下列一行程式碼中繼續，直到使用者關閉快顯功能表，或選取命令。 您可以使用它來顯示快顯功能表的替代方法是[CContextMenuManager::ShowPopupMenu](#showpopupmenu)。 該方法不是強制回應呼叫，而且不會傳回所選命令的識別碼。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
