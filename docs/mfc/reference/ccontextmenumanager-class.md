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
ms.openlocfilehash: c676355ebf44d6cc02bfa66ac870757627ae5a58
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754813"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 類別

物件`CContextMenuManager`管理快捷功能表,也稱為上下文菜單。

## <a name="syntax"></a>語法

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CContext 選單管理員:C上下文選單管理員](#ccontextmenumanager)|建構 `CContextMenuManager` 物件。|
|`CContextMenuManager::~CContextMenuManager`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CContext 選單管理員:新增選單](#addmenu)|添加新的快捷功能表。|
|[CContext 選單管理員::取得選單ById](#getmenubyid)|返回與提供的資源 ID 關聯的功能表的句柄。|
|[CContext 選單管理員::取得Menubyname](#getmenubyname)|返回與提供的功能表名稱匹配的菜單的句柄。|
|[CContext 選單管理員::取得選單名稱](#getmenunames)|傳回選單名稱的清單。|
|[CContext 選單管理員:載入狀態](#loadstate)|載入儲存在 Windows 註冊表中的快捷功能表。|
|[CContext 選單管理員::重置狀態](#resetstate)|從上下文菜單管理器清除快捷功能表。|
|[CContext 選單管理員::儲存狀態](#savestate)|將快捷功能表保存到 Windows 註冊表。|
|[CContext 選單管理員::設定不關閉活動選單](#setdontcloseactivemenu)|控制`CContextMenuManager`在 顯示新快捷功能表時,是否關閉活動快捷功能表。|
|[CContext 選單管理員::顯示彈出選單](#showpopupmenu)|顯示指定的快捷功能表。|
|[CContext 選單管理員::追蹤彈出選單](#trackpopupmenu)|顯示指定的快捷功能表。 返回所選功能表命令的索引。|

## <a name="remarks"></a>備註

`CContextMenuManager`管理快捷功能表並確保它們具有一致的外觀。

不應手動創建`CContextMenuManager`物件。 應用程式框架將建立物件`CContextMenuManager`。 但是,在初始化應用程式時,應調用[CWinAppEx:itContextMenuManager。](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 初始化上下文管理器後,使用方法[CWinAppEx::getContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)獲取指向應用程式的上下文管理器的指標。

您可以通過呼`AddMenu`叫 在執行時建立快捷選單。 如果要在未首先接收使用者輸入的情況下顯示選單,請呼叫`ShowPopupMenu`。 `TrackPopupMenu`在要創建功能表並等待使用者輸入時使用。 `TrackPopupMenu`如果使用者退出而不選擇任何內容,則返回所選命令的索引或 0。

`CContextMenuManager`還可以將其狀態保存並載入Windows註冊表。

## <a name="example"></a>範例

下面的範例展示如何向`CContextMenuManager`物件添加功能表,以及如何在`CContextMenuManager`物件顯示新的彈出式功能表時不關閉活動彈出式功能表。 此代碼段是[自定義頁示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>需求

**標題:** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContext 選單管理員:新增選單

加入[CContextMenu 管理員](../../mfc/reference/ccontextmenumanager-class.md)加入新的快捷選單。

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>參數

*uiMenuNameResid*<br/>
[在]包含新選單名稱的字串的資源 ID。

*uiMenuResId*<br/>
[在]功能表資源識別碼。

*lpsz名稱*<br/>
[在]包含新選單名稱的字串。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;如果方法失敗,為 0。

### <a name="remarks"></a>備註

如果*uiMenuResId*無效,或者同一名稱的另一個功能表已在`CContextMenuManager`中, 則此方法將失敗。

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContext 選單管理員:C上下文選單管理員

建構[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。

```
CContextMenuManager();
```

### <a name="remarks"></a>備註

在大多數情況下,不應手動創建。 `CContextMenuManager` 應用程式框架將建立物件`CContextMenuManager`。 您應該在應用程式的初始化期間調用[CWinAppEx:initContextMenuManager。](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 要取得指向上下文管理員的指標,請致電[CWinAppEx::取得ContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContext 選單管理員::取得選單ById

返回與給定資源 ID 關聯的功能表的句柄。

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>參數

*恩梅努雷斯Id*<br/>
[在]功能表的資源識別碼。

### <a name="return-value"></a>傳回值

關聯功能表的句柄或`NULL`找不到功能表。

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContext 選單管理員::取得Menubyname

將句柄返回到特定功能表。

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
[在]包含要檢索的功能表名稱的字串。

*普伊奧裡格雷斯ID*<br/>
[出]指向 UINT 的指標。 這裡包含指定選單的資源 ID(如果找到)。

### <a name="return-value"></a>傳回值

與*lpszName*指定的名稱符合的選單的句柄。 如果沒有名為*lpszName*的選單,則為 NULL。

### <a name="remarks"></a>備註

如果此方法找到與*lpszName*匹配的`GetMenuByName`選單 ,則將選單資源 ID 儲存在參數*puiOrigResID*中。

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContext 選單管理員::取得選單名稱

返回添加到[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)的功能表名稱清單。

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>參數

*名稱清單*<br/>
[出]對[CStringList](../../mfc/reference/cstringlist-class.md)參數的引用。 此方法將功能表名稱清單寫入此參數。

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContext 選單管理員:載入狀態

從 Windows 註冊表載入與[CContextMenuManager 類](../../mfc/reference/ccontextmenumanager-class.md)關聯的資訊。

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]包含註冊表項的相對路徑的字串。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

*lpszProfileName*參數不是註冊表項的絕對路徑。 它是添加到應用程式的預設註冊表項末尾的相對路徑。 要取得或設定預設註冊表項,請使用[CWinAppEx::取得註冊庫](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx::設定註冊表項的方法](../../mfc/reference/cwinappex-class.md#setregistrybase)。

使用方法[CContextMenuManager::儲存狀態](#savestate)以將快捷菜單保存到註冊表。

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContext 選單管理員::重置狀態

清除與[CContextMenuManager 類](../../mfc/reference/ccontextmenumanager-class.md)關聯的快捷功能表中的所有項。

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;如果發生故障,則 FALSE。

### <a name="remarks"></a>備註

此方法清除彈出式功能表並從 中`CContextMenuManager`刪除 它們。

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContext 選單管理員::儲存狀態

將與[CContextMenuManager 類](../../mfc/reference/ccontextmenumanager-class.md)關聯的資訊保存到 Windows 註冊表。

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]包含註冊表項的相對路徑的字串。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

*lpszProfileName*參數不是註冊表項的絕對路徑。 它是添加到應用程式的預設註冊表項末尾的相對路徑。 要取得或設定預設註冊表項,請使用[CWinAppEx::取得註冊庫](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx::設定註冊表項的方法](../../mfc/reference/cwinappex-class.md#setregistrybase)。

使用方法[CContextMenuManager:LoadState](#loadstate)從註冊表載入快捷選單。

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContext 選單管理員::設定不關閉活動選單

控制[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)在顯示新的彈出式功能表時是否關閉活動彈出式功能表。

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
[在]控制是否關閉活動彈出功能表的布林參數。 "TRUE"值表示活動彈出功能表未關閉。 FALSE 表示活動彈出視窗功能表已關閉。

### <a name="remarks"></a>備註

默認情況下,關閉`CContextMenuManager`活動彈出視窗功能表。

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContext 選單管理員::顯示彈出選單

顯示指定的快捷功能表。

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
[在]此方法將顯示的功能表的資源 ID。

*x*<br/>
[在]用戶端座標中快捷功能表的水準偏移。

*Y*<br/>
[在]用戶端座標中快捷選單垂直偏移

*pwndOwner*<br/>
[在]指向快捷功能表的父視窗的指標。

*bown消息*<br/>
[在]指示消息路由方式的布爾參數。 如果*bown 消息*為 FALSE,則使用標準 MFC 路由。 否則 *,pWndOwner*會接收消息。

*赫梅努普*<br/>
[在]此方法將顯示的功能表的句柄。

*bAuto銷毀*<br/>
[在]指示功能表是否將自動銷毀的布爾參數。

*b 右對齊*<br/>
[在]指示功能表項對齊方式的布爾參數。 如果*bRight 對齊*為 TRUE,則功能表在從右到左讀取順序時右對齊。

### <a name="return-value"></a>傳回值

如果該方法成功顯示功能表,則第一個方法重載將返回非零;否則 0。 如果快捷功能表顯示正確,則第二個方法重載返回指向[CMFCPopupMenu 的](../../mfc/reference/cmfcpopupmenu-class.md)指標;否則 NULL。

### <a name="remarks"></a>備註

此方法類似於方法[CContextMenuManager::TrackPopupMenu,](#trackpopupmenu)因為兩種方法都顯示一個快捷功能表。 但是,`TrackPopupMenu`返回所選功能表命令的索引。

如果參數*bAuto銷毀*是 FALSE,則必須手動`DestroyMenu`調用繼承 的方法來釋放記憶體資源。 預設`ShowPopupMenu`可使用參數*bAuto 銷毀*。 它供將來使用或用於從類派生的`CContextMenuManager`自定義類。

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContext 選單管理員::追蹤彈出選單

顯示指定的快捷功能表並返回所選快捷功能表命令的索引。

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>參數

*赫梅努普*<br/>
[在]此方法顯示的快捷功能表的句柄。

*x*<br/>
[在]用戶端座標中快捷功能表的水準偏移。

*Y*<br/>
[在]用戶端座標中快捷功能表的垂直偏移。

*pwndOwner*<br/>
[在]指向快捷功能表的父視窗的指標。

*b 右對齊*<br/>
[在]指示功能表項對齊方式的布爾參數。 如果*bRight 對齊*為 TRUE,則功能表在從右到左讀取順序時右對齊。 如果*bRightAlign*為 FALSE,則功能表在從左到右的閱讀順序中左對齊。

### <a name="return-value"></a>傳回值

用戶選擇的命令的功能表命令 ID;如果使用者在不選擇功能表命令的情況下關閉快捷功能表,則為 0。

### <a name="remarks"></a>備註

此方法用作顯示快捷功能表的模態調用。 在使用者關閉快捷功能表或選擇命令之前,應用程式不會繼續到代碼中的下一行。 可用於顯示快捷選單的替代方法是[CContextMenuManager::ShowPopupMenu](#showpopupmenu)。 該方法不是模態調用,不會返回所選命令的 ID。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
