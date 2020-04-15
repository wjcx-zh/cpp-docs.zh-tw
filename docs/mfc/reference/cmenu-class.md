---
title: CMenu 類別
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369972"
---
# <a name="cmenu-class"></a>CMenu 類別

Windows `HMENU`的封裝。

## <a name="syntax"></a>語法

```
class CMenu : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMenu:CMenu](#cmenu)|建構 `CMenu` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|將新專案追加到此功能表的末尾。|
|[CMenu::附加](#attach)|將 Windows 功能表句柄`CMenu`附加到 物件。|
|[CMenu::檢查選單專案](#checkmenuitem)|在彈出式功能表中,在菜單項旁邊放置複選標記或刪除複選標記。|
|[CMenu::檢查選單廣播專案](#checkmenuradioitem)|將單選按鈕放在菜單項旁邊,並從組中的所有其他功能表項中刪除單選按鈕。|
|[CMenu:建立選單](#createmenu)|創建一個空功能表並將其附加到`CMenu`物件。|
|[CMenu::建立彈出選單](#createpopupmenu)|創建一個空的彈出式功能表並將其附加到`CMenu`物件。|
|[CMenu::DeleteMenu](#deletemenu)|從選單中刪除指定的專案。 如果功能表項具有關聯的彈出式功能表,則銷毀彈出視窗功能表的句柄並釋放其使用的記憶體。|
|[CMenu::D](#deletetempmap)|刪除`FromHandle`成員函數創建`CMenu`的任何臨時物件。|
|[CMenu::D](#destroymenu)|銷毀附加到`CMenu`物件的功能表,並釋放菜單佔用的任何記憶體。|
|[CMenu::D埃塔奇](#detach)|從`CMenu`物件分離 Windows 功能表句柄並返回該句柄。|
|[CMenu::D原始專案](#drawitem)|當所有者繪製的功能表的可視方面發生更改時,由框架調用。|
|[CMenu:啟用選單專案](#enablemenuitem)|啟用、禁用或調暗(灰色)功能表項。|
|[CMenu::從手柄](#fromhandle)|返回指向給定 Windows`CMenu`功能表句柄的物件的指標。|
|[CMenu:取得預設項目](#getdefaultitem)|確定指定功能表上的預設選單項。|
|[CMenu:取得選單上下文說明 Id](#getmenucontexthelpid)|檢索與功能表關聯的説明上下文 ID。|
|[CMenu::取得選單資訊](#getmenuinfo)|檢索特定功能表上的資訊。|
|[CMenu:取得選單項目計數](#getmenuitemcount)|確定彈出視窗或頂級功能表中的項目數。|
|[CMenu:取得選單項目ID](#getmenuitemid)|獲取位於指定位置的功能表項的功能表項識別碼。|
|[CMenu:取得選單項目資訊](#getmenuiteminfo)|檢索有關功能表項的資訊。|
|[CMenu::取得選單](#getmenustate)|返回指定功能表項的狀態或彈出式功能表中的項數。|
|[CMenu::取得選單字串](#getmenustring)|檢索指定功能表項的標籤。|
|[CMenu:取得安全海選單](#getsafehmenu)|返回此`m_hMenu``CMenu`物件包裝。|
|[CMenu:抓取子選單](#getsubmenu)|檢索指向彈出功能表的指標。|
|[CMenu::InsertMenu](#insertmenu)|在指定位置插入新功能表項,將其他項向下移動功能表。|
|[CMenu:插入選單專案](#insertmenuitem)|在功能表中的指定位置插入新選單項。|
|[CMenu::載入選單](#loadmenu)|從可執行檔中載入選單資源並將其附加到`CMenu`物件。|
|[CMenu::載入選單間接](#loadmenuindirect)|從記憶體中的功能表範本載入功能表並將其附加到`CMenu`物件。|
|[CMenu:度量值項目](#measureitem)|由框架呼叫,以確定建立所有者繪製的功能表時的功能表維度。|
|[CMenu::ModifyMenu](#modifymenu)|在指定位置更改現有功能表項。|
|[CMenu::刪除選單](#removemenu)|從指定的功能表中刪除具有關聯彈出式功能表的功能表項。|
|[CMenu:設定預設項目](#setdefaultitem)|設置指定功能表的預設選單項。|
|[CMenu:設定選單上下文說明Id](#setmenucontexthelpid)|將説明上下文 ID 設置為與功能表關聯的説明上下文 ID。|
|[CMenu::設定選單資訊](#setmenuinfo)|設置特定功能表上的資訊。|
|[CMenu::設定選單項目點陣圖](#setmenuitembitmaps)|將指定的複選位圖與功能表項目關聯。|
|[CMenu::設定選單項目資訊](#setmenuiteminfo)|更改有關功能表項的資訊。|
|[CMenu::追蹤彈出選單](#trackpopupmenu)|在指定位置顯示浮動彈出式功能表,並跟蹤彈出功能表上的項目選擇。|
|[CMenu::追蹤彈出選單Ex](#trackpopupmenuex)|在指定位置顯示浮動彈出式功能表,並跟蹤彈出功能表上的項目選擇。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMenu::操作員 HMENU](#operator_hmenu)|檢索功能表物件的句柄。|
|[CMenu::操作員!*](#operator_neq)|確定兩個功能表物件是否相等。|
|[CMenu::運算符 |](#operator_eq_eq)|確定兩個功能表物件是否相等。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|指定附加到物件的 Windows 選`CMenu`單的句柄。|

## <a name="remarks"></a>備註

它提供了用於創建、跟蹤、更新和銷毀功能表的成員函數。

在堆`CMenu`棧幀上創建一個對象作為本地`CMenu`,然後調用的成員函數根據需要操作新功能表。 接下來,調用[CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu)將功能表設置為視窗,然後立即`CMenu`調用 物件的[「分離](#detach)」成員函數。 成員`CWnd::SetMenu`函數將視窗的功能表設置為新功能表,使視窗重新繪製以反映功能表更改,並將功能表的所有權傳遞給視窗。 調用`Detach``CMenu`從 物件分離 HMENU,`CMenu`以便在局部 變數超過`CMenu`範圍時, 物件析構函數不會嘗試銷毀它不再擁有的菜單。 當視窗被破壞時,功能表本身會自動銷毀。

您可以使用[LoadMenu 間接](#loadmenuindirect)成員函數從記憶體中的範本創建選單,但更容易維護由調用[LoadMenu](#loadmenu)從資源創建的功能表,並且功能表資源管理器可以創建和修改選單資源本身。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu::附加選單

將新專案追加到菜單的末尾。

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>參數

*nFlags*<br/>
指定新功能表項添加到功能表時的狀態資訊。 它由「備註」部分中列出的一個或多個值組成。

*nIDNewItem*<br/>
指定新選單項目的指令代碼,或是如果*nFlags*設定為MF_POPUP,則指定彈出選單的選`HMENU`單 句柄 ( ) 。 如果將 nFlags 設置為MF_SEPARATOR,則忽略 *(不需要)nIDNewItem*參數。 *nFlags*

*lpszNewItem*<br/>
指定新功能表項的內容。 *nFlags*參數用於以下列方式解釋*lpszNewItem:*

|nFlags|lpszNewItem 的解釋|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含應用程式提供的 32 位值,應用程式可以使用該值來維護與功能表項關聯的其他數據。 當應用程式處理WM_MEASUREITEM和WM_DRAWITEM消息時,此 32 位值可供應用程式使用。 該值存儲在這些消息提供`itemData`的結構成員中。|
|MF_STRING|包含指向 null 終止字串的指標。 這是默認解釋。|
|MF_SEPARATOR|*lpszNewItem 參數*將被忽略(不需要)。|

*pBmp*<br/>
指向將用作`CBitmap`功能表項的物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以通過在*nFlags*中設置值來指定功能表項的狀態。 當*nIDNewItem*指定一個彈出式功能表時,它將成為附加該功能表的一部分。 如果該功能表被銷毀,則附加的功能表也將銷毀。 附加的功能表應與物件分離以避免`CMenu`衝突。 請注意,MF_STRING和MF_OWNERDRAW對`AppendMenu`的 位圖版本無效。

以下清單描述以*nFlags*中設定的旗標 :

- MF_CHECKED充當帶有MF_UNCHECKED的切換,將默認複選標記放在項旁邊。 當應用程式提供複選標記位圖(請參閱[SetMenuItemBitmap](#setmenuitembitmaps)成員函數)時,將顯示"複選標記"位圖。

- MF_UNCHECKED充當帶有MF_CHECKED的切換,以刪除專案旁邊的複選標記。 當應用程式提供複選標記位圖(請參閱`SetMenuItemBitmaps`成員函數)時,將顯示「複選標記關閉」位圖。

- MF_DISABLED禁用功能表項,使其無法選擇,但不會將其變暗。

- MF_ENABLED 啟用功能表項,以便可以選擇菜單項並將其從調光狀態還原。

- MF_GRAYED禁用功能表項,使其無法選中並調暗。

- MF_MENUBARBREAK將專案放在靜態功能表中的新行上,或在彈出式功能表中的新列中放置。 新的彈出式功能表列將與舊列分開,由垂直分隔線分隔。

- MF_MENUBREAK將專案放在靜態功能表中的新行上,或在彈出式功能表中的新列中放置。 列之間沒有放置分界線。

- MF_OWNERDRAW 指定該專案是擁有者繪製項。 首次顯示功能表時,擁有功能表的視窗將接收WM_MEASUREITEM消息,該消息檢索功能表項的高度和寬度。 當所有者必須更新功能表項的可視外觀時,WM_DRAWITEM消息是發送的消息。 此選項對頂級功能表項無效。

- MF_POPUP 指定功能表項具有與其關聯的彈出式功能表。 ID 參數指定要與項關聯的彈出式功能表的句柄。 這用於將頂級彈出式功能表或分層彈出式功能表添加到彈出式功能表項。

- MF_SEPARATOR繪製水準分界線。 只能在彈出式功能表中使用。 無法調暗、禁用或突出顯示此行。 其他參數將被忽略。

- MF_STRING 指定選單項目是字串。

以下每個組都列出互斥且不能一起使用的標誌:

- MF_DISABLED、MF_ENABLED和MF_GRAYED

- MF_STRING、MF_OWNERDRAW、MF_SEPARATOR和位圖版本

- MF_MENUBARBREAK和MF_MENUBREAK

- MF_CHECKED和MF_UNCHECKED

每當位於視窗中的選單發生變更(無論是否顯示視窗),應用程式都應呼叫[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>範例

  請參閱[CMenu::createMenu](#createmenu)的範例。

## <a name="cmenuattach"></a><a name="attach"></a>CMenu::附加

將現有的 Windows 功能表`CMenu`附加到 物件。

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
指定 Windows 選單的句柄。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

如果選單已附加到物件,`CMenu`則不應呼叫此功能。 選單句柄儲存在資料成員中`m_hMenu`。

如果要操作的功能表已與視窗關聯,則可以使用[CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函數獲取功能表的句柄。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::檢查選單專案

向彈出式功能表中的功能表項添加複選標記或刪除檢查標記。

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>參數

*nID檢查專案*<br/>
指定要檢查的功能表項,由*nCheck*確定。

*N檢查*<br/>
指定如何檢查功能表項以及如何確定專案在功能表中的位置。 *nCheck*參數可以是具有MF_BYPOSITION或MF_BYCOMMAND標誌的MF_CHECKED或MF_UNCHECKED的組合。 可以使用位或運算符組合這些標誌。 它們具有以下含義:

- MF_BYCOMMAND 指定參數提供現有功能表項的命令 ID。 這是預設值。

- MF_BYPOSITION 指定參數給出現有功能表項的位置。 第一個項目位於位置 0。

- MF_CHECKED充當帶有MF_UNCHECKED的切換,將默認複選標記放在項旁邊。

- MF_UNCHECKED充當帶有MF_CHECKED的切換,以刪除專案旁邊的複選標記。

### <a name="return-value"></a>傳回值

項的上一個狀態:MF_CHECKED或MF_UNCHECKED,或者如果菜單項不存在,則為 0xFFFFFFFFFF。

### <a name="remarks"></a>備註

*nIDCheckItem 參數*指定要修改的項。

*nIDCheckItem*參數可以標識彈出功能表項以及功能表項。 無需執行特殊步驟即可檢查彈出式功能表項。 無法檢查頂級功能表項。 必須按位置檢查彈出式功能表項,因為它沒有與其關聯的菜單項標識符。

### <a name="example"></a>範例

  請參考[CMenu::GetMenustate 的範例](#getmenustate)。

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::檢查選單廣播專案

檢查指定的功能表項,使其成為一個單選項。

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*nID 第一*<br/>
指定(作為 ID 或偏移,具體取決於*nFlags*的值)單選按鈕組中的第一個功能表項。

*nIDLast*<br/>
指定(作為 ID 或偏移量,具體取決於*nFlags*的值)單選按鈕組中的最後一個功能表項。

*nIDItem*<br/>
指定(作為 ID 或偏移,具體取決於*nFlags*的值),組中將用單選按鈕檢查的項。

*nFlags*<br/>
以下列方式指定*nIDFirst、nIDLast*和*nIDItem*的解釋: *nIDLast*

|nFlags|解譯|
|------------|--------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。|

### <a name="return-value"></a>傳回值

如果成功,則非零;否則 0

### <a name="remarks"></a>備註

同時,函數將取消檢查關聯組中的所有其他功能表項,並清除這些專案的廣播項類型標誌。 選中的專案使用單選按鈕(或項目符號)位圖而不是複選標記位圖顯示。

### <a name="example"></a>範例

  請參閱[ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)的示例。

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu:CMenu

創建一個空功能表並將其附加到`CMenu`物件。

```
CMenu();
```

### <a name="remarks"></a>備註

在呼叫`CMenu:`

- [建立選單](#createmenu)

- [建立彈出選單](#createpopupmenu)

- [載入選單](#loadmenu)

- [載入選單間接](#loadmenuindirect)

- [附加](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu:建立選單

創建功能表並將其附加到`CMenu`物件。

```
BOOL CreateMenu();
```

### <a name="return-value"></a>傳回值

如果已成功創建功能表,則非零;否則 0。

### <a name="remarks"></a>備註

功能表最初為空。 可以使用`AppendMenu``InsertMenu`或成員函數添加功能表項。

如果功能表分配給視窗,則當視窗被銷毀時,它會自動銷毀。

在退出之前,如果功能表未分配給視窗,則應用程式必須釋放與菜單關聯的系統資源。 應用程式通過調用[銷毀功能表](#destroymenu)成員函數釋放功能表。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::建立彈出選單

創建一個彈出式功能表並將其附加到`CMenu`物件。

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>傳回值

成功創建彈出式功能表時非零;否則 0。

### <a name="remarks"></a>備註

功能表最初為空。 可以使用`AppendMenu``InsertMenu`或成員函數添加功能表項。 應用程式可以將彈出式功能表添加到現有功能表或彈出式功能表。 成員`TrackPopupMenu`函數可用於將此功能表顯示為浮動彈出式功能表,並跟蹤彈出式功能表上的選擇。

如果功能表分配給視窗,則當視窗被銷毀時,它會自動銷毀。 如果功能表添加到現有功能表中,則當該功能表被銷毀時,該功能表將自動銷毀。

在退出之前,如果功能表未分配給視窗,則應用程式必須釋放與彈出式功能表關聯的系統資源。 應用程式通過調用[銷毀功能表](#destroymenu)成員函數釋放功能表。

### <a name="example"></a>範例

  請參閱[CMenu::createMenu](#createmenu)的範例。

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu::DeleteMenu

從選單中刪除專案。

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*n位置*<br/>
指定要刪除的功能表項,由*nFlags*確定。

*nFlags*<br/>
在以下欄方式解釋*n 定位*:

|nFlags|N 定位的解釋|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。|

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

如果功能表項具有關聯的彈出式功能表,則`DeleteMenu`銷毀彈出視窗功能表的句柄並釋放彈出功能表使用的記憶體。

每當位於視窗中的選單發生變更(無論是否顯示視窗),應用程式都必須呼叫[CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>範例

  請參閱[CWnd 的範例::取得選單](../../mfc/reference/cwnd-class.md#getmenu)。

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::D

由`CWinApp`空閑時間處理程式自動調用,刪除[FromHandle](#fromhandle)成員`CMenu`函數創建的任何臨時物件。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>備註

`DeleteTempMap`在刪除`CMenu``CMenu`物件之前,分離附加到臨時物件的 Windows 功能表物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::D

銷毀功能表和已使用的任何 Windows 資源。

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>傳回值

如果功能表已銷毀,則非零;否則 0。

### <a name="remarks"></a>備註

功能表在銷毀之前與`CMenu`物件分離。 析`CMenu`構`DestroyMenu`函數中會自動調用 Windows 函數。

### <a name="example"></a>範例

  請參閱[CMenu::createMenu](#createmenu)的範例。

## <a name="cmenudetach"></a><a name="detach"></a>CMenu::D埃塔奇

從`CMenu`物件分離 Windows 功能表並返回句柄。

```
HMENU Detach();
```

### <a name="return-value"></a>傳回值

HMENU 類型的句柄(如果成功)到 Windows 功能表;否則 NULL。

### <a name="remarks"></a>備註

資料`m_hMenu`成員設定為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu::D原始專案

當所有者繪製的功能表的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標,其中包含有關所需繪圖類型的資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構`itemAction`的成員定義要執行的繪圖操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CMenu`。 應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

有關`DRAWITEMSTRUCT`結構的說明,請參閱[CWnd:OnDrawItem。](../../mfc/reference/cwnd-class.md#ondrawitem)

### <a name="example"></a>範例

以下代碼來自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)範例:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu:啟用選單專案

啟用、禁用或調暗功能表項。

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>參數

*nID 啟用項目*<br/>
指定要啟用的功能表項,由*nEnable*確定。 此參數可以指定彈出式功能表項以及標準功能表項。

*n 啟用*<br/>
指定要執行的操作。 它可以是MF_DISABLED、MF_ENABLED或MF_GRAYED的組合,具有MF_BYCOMMAND或MF_BYPOSITION。 可以使用位或運算符組合這些值。 這些值具有以下意義：

- MF_BYCOMMAND 指定參數提供現有功能表項的命令 ID。 這是預設值。

- MF_BYPOSITION 指定參數給出現有功能表項的位置。 第一個項目位於位置 0。

- MF_DISABLED禁用功能表項,使其無法選擇,但不會將其變暗。

- MF_ENABLED 啟用功能表項,以便可以選擇菜單項並將其從調光狀態還原。

- MF_GRAYED禁用功能表項,使其無法選中並調暗。

### <a name="return-value"></a>傳回值

以前的狀態(MF_DISABLED、MF_ENABLED 或MF_GRAYED)或 -1(如果無效)。

### <a name="remarks"></a>備註

[CreateMenu、InsertMenu、](#createmenu)[修改選單](#modifymenu)和[LoadMenu 間接](#loadmenuindirect)成員函數還可以設置功能表項的狀態(已啟用、禁用[InsertMenu](#insertmenu)或調暗)。

使用MF_BYPOSITION值需要應用程式使用正確的`CMenu`。 如果使用菜單`CMenu`欄,則影響頂級菜單項(功能表欄中的項)。 要按位置設置彈出視窗或嵌套彈出式功能表中專案的狀態,應用程式必須指定彈出式功能表的。 `CMenu`

當應用程式指定MF_BYCOMMAND標誌時,Windows會檢查隸屬於`CMenu`的彈出功能表項。因此,除非存在重複的菜單項,`CMenu`否則使用菜單欄就足夠了。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu::從手柄

將指向給定 Windows`CMenu`句柄的物件的指標返回到功能表。

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
功能表的 Windows 句柄。

### <a name="return-value"></a>傳回值

指向`CMenu`的指標可能是臨時的或永久性的。

### <a name="remarks"></a>備註

如果物件`CMenu`尚未附加到 Windows 功能表物件,則創建`CMenu`並附加臨時 物件。

此臨時`CMenu`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時物件。

### <a name="example"></a>範例

  請參閱[CMenu::createMenu](#createmenu)的範例。

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu:取得預設項目

確定指定功能表上的預設選單項。

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*格迪旗*<br/>
指定函數如何搜索功能表項的值。 這個參數可以是無、一個或以下值的組合:

|值|意義|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|指定,如果預設項是打開子功能表的項,則函數將在相應的子菜單中重播地搜索。 如果子功能表沒有預設項,則返回值標識打開子功能表的項。<br /><br /> 默認情況下,該函數返回指定功能表上的第一個預設項,而不管它是否是打開子菜單的項。|
|GMDI_USEDISABLED|指定函數要返回預設項,即使它已禁用也是如此。<br /><br /> 默認情況下,該函數跳過禁用或灰顯的專案。|

*fByPos*<br/>
指定是檢索功能表項的標識符還是其位置的值。 如果此參數為 FALSE,則返回標識符。 否則,將返回該位置。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值是菜單項的標識符或位置。 如果函數失敗,返回值為 - 1。

### <a name="remarks"></a>備註

此成員函數實現 Win32 函數[GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu:取得選單上下文說明 Id

檢索與`CMenu`關聯的上下文幫助 ID。

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>傳回值

內容說明 ID 目前`CMenu`與關聯(如果有)零否則。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::取得選單資訊

檢索功能表的資訊。

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>參數

*lpcmi*<br/>
指向[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)結構的指標,其中包含功能表的資訊。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值為非零;否則,返回值為零。

### <a name="remarks"></a>備註

調用此函數以檢索有關功能表的資訊。

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu:取得選單項目計數

確定彈出視窗或頂級功能表中的項目數。

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>傳回值

如果函數成功,則功能表中的項數;否則 -1。

### <a name="example"></a>範例

  請參閱[CWnd 的範例::取得選單](../../mfc/reference/cwnd-class.md#getmenu)。

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu:取得選單項目ID

獲取位於*nPos*定義位置的選單項的功能表項識別碼。

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定正在檢索其 ID 的功能表項的位置(從零開始)。

### <a name="return-value"></a>傳回值

如果函數成功,則彈出功能表中指定項的項目 ID。 如果指定的項是彈出式功能表(與彈出功能表中的項相反),則返回值為 -1。 如果*nPos*對應於 SEPARATOR 功能表項,則返回值為 0。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu:取得選單項目資訊

檢索有關功能表項的資訊。

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
要獲取有關獲取資訊的功能表項的標識符或位置。 這裡參數的含義取的值`ByPos`。

*lpMenu 專案資訊*<br/>
指向[MenuITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow)的指標,如 Windows SDK 中所述,其中包含有關功能表的資訊。

*fByPos*<br/>
指定`nIDItem`的含義的值。 預設情況下,FALSE`ByPos`表示 uItem 是功能表項識別碼。 如果未`ByPos`設置為 FALSE,則指示功能表項位置。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值為非零。 如果此函式失敗，則傳回值為零。 要取得延伸的錯誤資訊,請使用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror),如 Windows SDK 中所述。

### <a name="remarks"></a>備註

此成員函數實現 Win32 函數[GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)的行為,如 Windows SDK 中所述。 請注意,在 MFC`GetMenuItemInfo`實現 中,您不使用對功能表的句柄。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::取得選單

返回指定功能表項的狀態或彈出式功能表中的項數。

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
指定功能表項 ID,由*nFlags*確定。

*nFlags*<br/>
指定*nID*的性質 。 它可能是下列其中一個值：

- MF_BYCOMMAND 指定參數提供現有功能表項的命令 ID。 這是預設值。

- MF_BYPOSITION 指定參數給出現有功能表項的位置。 第一個項目位於位置 0。

### <a name="return-value"></a>傳回值

如果指定的項不存在,則值 0xFFFFFFFFFFFFFF。 如果*nId*標識了彈出式功能表,則高階位元組包含彈出式功能表中的項數,低階字節包含與彈出式功能表關聯的功能表標誌。 否則,傳回值是以下清單中值的掩碼 (Boolean OR)(此遮罩描述*nId*識別的選單狀態):

- MF_CHECKED充當帶有MF_UNCHECKED的切換,將默認複選標記放在項旁邊。 當應用程式提供複選標記位圖(請參閱`SetMenuItemBitmaps`成員函數)時,將顯示「複選標記」位圖。

- MF_DISABLED禁用功能表項,使其無法選擇,但不會將其變暗。

- MF_ENABLED 啟用功能表項,以便可以選擇菜單項並將其從調光狀態還原。 請注意,此常量的值為 0;因此,此常量的值為 0。使用此值時,應用程式不應針對 0 測試失敗。

- MF_GRAYED禁用功能表項,使其無法選中並調暗。

- MF_MENUBARBREAK將專案放在靜態功能表中的新行上,或在彈出式功能表中的新列中放置。 新的彈出式功能表列將與舊列分開,由垂直分隔線分隔。

- MF_MENUBREAK將專案放在靜態功能表中的新行上,或在彈出式功能表中的新列中放置。 列之間沒有放置分界線。

- MF_SEPARATOR繪製水準分界線。 只能在彈出式功能表中使用。 無法調暗、禁用或突出顯示此行。 其他參數將被忽略。

- MF_UNCHECKED充當帶有MF_CHECKED的切換,以刪除專案旁邊的複選標記。 當應用程式提供複選標記位圖(請參閱`SetMenuItemBitmaps`成員函數)時,將顯示「複選標記關閉」位圖。 請注意,此常量的值為 0;因此,此常量的值為 0。使用此值時,應用程式不應針對 0 測試失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::取得選單字串

將指定功能表項的標籤複製到指定的緩衝區。

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>參數

*nIDItem*<br/>
指定功能表項的整數識別碼或選單中的選單項目的偏移量,具體取決於*nFlags*的值。

*lpString*<br/>
指向要接收標籤的緩衝區。

*rString*<br/>
對要接收複製`CString`的功能表字串的物件的引用。

*nMax( N) Count*<br/>
指定要複製的標籤的最大長度(以字元表示)。 如果標籤長於*nMaxCount*中指定的最大值,則額外的字元將被截斷。

*nFlags*<br/>
指定*nIDItem*參數的解釋。 它可能是下列其中一個值：

|nFlags|NIDItem 的解釋|
|------------|-------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。|

### <a name="return-value"></a>傳回值

指定複製到緩衝區的實際字元數,不包括空終止符。

### <a name="remarks"></a>備註

*nMaxCount*參數應大於標籤中的字元數,以適應終止字串的空字元。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu:取得安全海選單

返回由此`CMenu`物件包裹的 HMENU 或`CMenu`NULL 指標。

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>範例

  請參閱[CMenu::LoadMenu](#loadmenu)的範例。

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu:抓取子選單

檢索彈出式功能表`CMenu`的物件。

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定選單中包含的彈出式功能表的位置。 對於第一個功能表項,位置值從 0 開始。 在此函數中不能使用彈出式功能表的標識碼。

### <a name="return-value"></a>傳回值

指向物件(`CMenu`如果給定`m_hMenu`位置 存在彈出選單)時,其成員包含對彈出選單的句柄的指標;否則 NULL。 如果`CMenu`物件不存在,則創建臨時物件。 不應`CMenu`存儲返回的指標。

### <a name="example"></a>範例

  請參考[CMenu 表示:追蹤器的追蹤器](#trackpopupmenu):

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu:插入選單

在*n 定位*指定的位置插入新選單項,並將其他項移下功能表。

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>參數

*n位置*<br/>
指定要插入新功能表項之前的選單項。 *nFlags*參數可用於以下方式解釋*n定位*:

|nFlags|N 定位的解釋|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。 如果*n 定位*為 -1,則新功能表項將追加到菜單的末尾。|

*nFlags*<br/>
指定如何解釋*n 定位,* 並指定新選單項目加入選單時的狀態資訊。 有關可能設置的標誌的清單,請參閱[AppendMenu](#appendmenu)成員函數。 要指定多個值,請使用位或運算元將它們與MF_BYCOMMAND或MF_BYPOSITION標誌組合。

*nIDNewItem*<br/>
指定新功能表項的命令 ID,或者,如果*nFlags*設定為MF_POPUP,則指定彈出選單的選單句柄 (HMENU)。 如果將 nFlags 設置為MF_SEPARATOR,則忽略 *(不需要)nIDNewItem*參數。 *nFlags*

*lpszNewItem*<br/>
指定新功能表項的內容。 *nFlags*可用於以以下方式解釋*lpszNewItem:*

|nFlags|lpszNewItem 的解釋|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含應用程式提供的 32 位值,應用程式可以使用該值來維護與功能表項關聯的其他數據。 此 32 位值可用於[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)`itemData`和[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)消息提供的結構成員中的應用程式。 這些消息在最初顯示或更改功能表項時發送。|
|MF_STRING|包含指向 null 終止字串的長指標。 這是默認解釋。|
|MF_SEPARATOR|*lpszNewItem 參數*將被忽略(不需要)。|

*pBmp*<br/>
指向將用作`CBitmap`功能表項的物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以通過在*nFlags*中設置值來指定功能表項的狀態。

您可以顯示視窗中的選單發生變更(無論是否顯示視窗),應用程式都應呼叫`CWnd::DrawMenuBar`。

當*nIDNewItem*指定一個彈出式功能表時,它將成為插入該功能表的菜單的一部分。 如果該功能表已銷毀,則插入的菜單也將銷毀。 插入的功能表應從`CMenu`物件分離以避免衝突。

如果活動多個文檔介面 (MDI) 子視窗最大化,並且應用程式透過調用此函數並指定MF_BYPOSITION標誌將彈出選單插入到 MDI 應用程式的選單中,則功能表將插入比預期更遠的位置。 這是因為活動 MDI 子視窗的控制選單插入到 MDI 框架視窗功能表欄的第一個位置。 要正確放置功能表,應用程式必須向其他使用的位置值添加1。 應用程式可以使用WM_MDIGETACTIVE消息來確定當前活動的子視窗是否最大化。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu:插入選單專案

在功能表中的指定位置插入新選單項。

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
請參閱 Windows SDK 中的[插入選單項目](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)中的*u 專案*說明。

*lpMenu 專案資訊*<br/>
請參閱 Windows SDK 中`InsertMenuItem` *lpmii*的說明。

*fByPos*<br/>
請參閱 Windows SDK 中的`InsertMenuItem` *fBy 定位*說明。

### <a name="remarks"></a>備註

此函數包裝[InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw),在Windows SDK中描述。

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::載入選單

從應用程式的可執行檔載入功能表資源並將其附加到`CMenu`物件。

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpsz 資源名稱*<br/>
包含包含要載入的選單資源名稱的 null 連接端的字串。

*nID資源*<br/>
指定要載入的功能表資源的功能表 ID。

### <a name="return-value"></a>傳回值

如果功能表資源已成功載入,則非零;否則 0。

### <a name="remarks"></a>備註

在退出之前,如果功能表未分配給視窗,則應用程式必須釋放與菜單關聯的系統資源。 應用程式通過調用[銷毀功能表](#destroymenu)成員函數釋放功能表。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::載入選單間接

從記憶體中的功能表範本載入資源並將其附加到`CMenu`物件。

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>參數

*lpMenu 範本*<br/>
指向功能表範本(這是單個[功能表專案範本](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader)結構以及一個或多個[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)結構的集合)。 有關這兩個結構的詳細資訊,請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

如果功能表資源已成功載入,則非零;否則 0。

### <a name="remarks"></a>備註

功能表範本是一個標頭,後跟一個或多個[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)結構的集合,每個結構可能包含一個或多個功能表項和彈出功能表。

版本號應為 0。

標誌`mtOption`應包括彈出清單中最後一個專案和主清單中的最後一項MF_END。 有關其他`AppendMenu`標誌,請參閱成員函數。 在`mtId``mtOption`中 指定MF_POPUP時,必須從 MENUITEMTEMPLATE 結構中省略該成員。

為 MENUITEMTEMPLATE 結構分配的空間必須足夠大`mtString`,以便將功能表項的名稱作為 null 終止字串。

在退出之前,如果功能表未分配給視窗,則應用程式必須釋放與菜單關聯的系統資源。 應用程式通過調用[銷毀功能表](#destroymenu)成員函數釋放功能表。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu

指定附加到物件的 Windows 選`CMenu`單的 HMENU 句柄。

```
HMENU m_hMenu;
```

### <a name="example"></a>範例

  請參閱[CMenu::LoadMenu](#loadmenu)的範例。

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu:度量值項目

創建具有擁有者繪製樣式的功能表時,由框架調用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lp 測量項目結構*<br/>
指向結構的`MEASUREITEMSTRUCT`指標。

### <a name="remarks"></a>備註

默認情況下,此成員函數不執行任何操作。 覆蓋此成員函數並填充`MEASUREITEMSTRUCT`結構以通知 Windows 功能表的尺寸。

有關`MEASUREITEMSTRUCT`結構的說明,請參閱[CWnd:onMeasureItem。](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>範例

以下代碼來自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)範例:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::修改選單

在*n 定位*指定的位置更改現有選單項。

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>參數

*n位置*<br/>
指定要更改的功能表項。 *nFlags*參數可用於以下方式解釋*n定位*:

|nFlags|N 定位的解釋|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。|

*nFlags*<br/>
指定如何解釋*n定位*,並提供有關要對功能表項所做的更改的資訊。 有關可能設置的標誌清單,請參閱[AppendMenu](#appendmenu)成員函數。

*nIDNewItem*<br/>
指定修改選單項的命令 ID,或者,如果*nFlags*設置為MF_POPUP,則指定彈出式功能表的選單句柄 (HMENU)。 如果將 nFlags 設置為MF_SEPARATOR,則忽略 *(不需要)nIDNewItem*參數。 *nFlags*

*lpszNewItem*<br/>
指定新功能表項的內容。 *nFlags*參數可用於以以下方式解釋*lpszNewItem:*

|nFlags|lpszNewItem 的解釋|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含應用程式提供的 32 位值,應用程式可以使用該值來維護與功能表項關聯的其他數據。 當應用程式處理MF_MEASUREITEM和MF_DRAWITEM時,此 32 位值可供應用程式使用。|
|MF_STRING|包含指向 null 終止字串或的`CString`長指標。|
|MF_SEPARATOR|*lpszNewItem 參數*將被忽略(不需要)。|

*pBmp*<br/>
指向將用作`CBitmap`功能表項的物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式通過在*nFlags*中設置值來指定功能表項的新狀態。 如果此函數替換與功能表項關聯的彈出式功能表,它將銷毀舊的彈出式功能表並釋放彈出式功能表使用的記憶體。

當*nIDNewItem*指定一個彈出式功能表時,它將成為插入該功能表的菜單的一部分。 如果該功能表已銷毀,則插入的菜單也將銷毀。 插入的功能表應從`CMenu`物件分離以避免衝突。

您可以顯示視窗中的選單發生變更(無論是否顯示視窗),應用程式都應呼叫`CWnd::DrawMenuBar`。 要更改現有功能表項的屬性,使用`CheckMenuItem`和`EnableMenuItem`成員函數要快得多。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::操作員 HMENU

使用此運算符檢索`CMenu`物件的句柄。

```
operator HMENU() const;
```

### <a name="return-value"></a>傳回值

如果成功,則處理`CMenu`物件的句柄;否則,NULL。

### <a name="remarks"></a>備註

您可以使用該句柄直接呼叫 Windows API。

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu::操作員!*

確定兩個功能表在邏輯上是否相等。

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>參數

*選單*<br/>
要比較的 `CMenu` 物件。

### <a name="remarks"></a>備註

測試左側的功能表物件是否不等於右側的功能表物件。

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::運算符 |

確定兩個功能表在邏輯上是否相等。

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>參數

*選單*<br/>
要比較的 `CMenu` 物件。

### <a name="remarks"></a>備註

測試左側的功能表物件與右側的功能表物件是否相等(就HMENU值而言)。

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu::刪除選單

從功能表中刪除具有關聯彈出式功能表的功能表項。

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*n位置*<br/>
指定要刪除的選單項。 *nFlags*參數可用於以下方式解釋*n定位*:

|nFlags|N 定位的解釋|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。|

*nFlags*<br/>
指定如何解釋*n 定位*。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

它不會破壞彈出式功能表的句柄,因此功能表可以重複使用。 在調用此函數之前,應用程式可以調用`GetSubMenu`成員函數來檢索彈`CMenu`出 物件以供重用。

您可以顯示視窗中的選單發生變更(無論是否顯示視窗),應用程式都必須呼叫`CWnd::DrawMenuBar`。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu:設定預設項目

設置指定功能表的預設選單項。

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
新預設選單項目的識別碼或位置, 或 - 1,表示沒有預設項。 此參數的含義取決於*fByPos*的值。

*fByPos*<br/>
指定*uItem*的含義的值。 如果此參數為 FALSE,*則 uItem*是選單項識別碼。 否則,它是功能表項位置。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值為非零。 如果此函式失敗，則傳回值為零。 要取得延伸的錯誤資訊,請使用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror),如 Windows SDK 中所述。

### <a name="remarks"></a>備註

此成員函數實現 Win32 函數[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu:設定選單上下文說明Id

將上下文幫助`CMenu`ID 與 關聯。

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>參數

*dwContextHelpId*<br/>
要與`CMenu`關聯的上下文幫助 ID。

### <a name="return-value"></a>傳回值

如果成功,則非零;否則 0

### <a name="remarks"></a>備註

選單中的所有項都共用此識別符 - 無法將説明上下文標識符附加到各個功能表項。

### <a name="example"></a>範例

  請參閱[CMenu::插入功能表](#insertmenu)的範例。

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::設定選單資訊

設置功能表的資訊。

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>參數

*lpcmi*<br/>
指向[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)結構的指標,其中包含功能表的資訊。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值為非零;否則,返回值為零。

### <a name="remarks"></a>備註

調用此函數以設置有關功能表的特定資訊。

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::設定選單項目點陣圖

將指定的位圖與功能表與功能表。

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>參數

*n位置*<br/>
指定要更改的功能表項。 *nFlags*參數可用於以下方式解釋*n定位*:

|nFlags|N 定位的解釋|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項的命令 ID。 如果未設置MF_BYCOMMAND或MF_BYPOSITION,則這是預設值。|
|MF_BYPOSITION|指定參數給出現有功能表項的位置。 第一個項目位於位置 0。|

*nFlags*<br/>
指定如何解釋*n 定位*。

*pBmp 未選取*<br/>
指定未選取的選單項目要使用的點陣圖。

*pBmpChecked*<br/>
指定要用於選中的功能表項的點陣圖。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

無論功能表項是選中還是未選中,Windows都會在菜單項旁邊顯示相應的位圖。

如果*pBmpUnchecked*或*pBmpChecked*為 NULL,則 Windows 在相應屬性的功能表項旁邊不顯示任何內容。 如果兩個參數都是 NULL,則 Windows 在檢查專案時使用預設複選標記,並在取消選中專案時刪除複選標記。

當功能表被銷毀時,這些位圖不會被銷毀;但是,這些位圖不會被銷毀。應用程式必須銷毀它們。

Windows`GetMenuCheckMarkDimensions`函數檢索用於功能表項的預設複選標記的尺寸。 應用程式使用這些值來確定此函數提供的位圖的適當大小。 獲取大小,創建位圖,然後設置它們。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::設定選單項目資訊

更改有關功能表項的資訊。

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
請參閱 Windows SDK 中的[「SetMenuItemInfo」](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)中的*u 專案*說明。

*lpMenu 專案資訊*<br/>
請參閱 Windows SDK 中`SetMenuItemInfo` *lpmii*的說明。

*fByPos*<br/>
請參閱 Windows SDK 中的`SetMenuItemInfo` *fBy 定位*說明。

### <a name="remarks"></a>備註

此函數包裝在 Windows SDK 中描述的[SetMenuItemInfo。](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::追蹤彈出選單

在指定位置顯示浮動彈出式功能表,並跟蹤彈出功能表上的項目選擇。

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>參數

*nFlags*<br/>
指定螢幕位置和滑鼠位置標誌。 有關可用標誌的清單,請參閱[TrackPopupMenu。](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)

*X.*<br/>
指定彈出式功能表的螢幕座標中的水準位置。 根據*nFlags*參數的值,功能表可以左對齊、右對齊或相對於此位置居中。

*Y*<br/>
指定螢幕座標中螢幕座標中的垂直位置。

*pwnd*<br/>
標識擁有彈出式功能表的視窗。 即使指定了TPM_NONOTIFY標誌,此參數也不能為 NULL。 此視窗從功能表接收所有WM_COMMAND消息。 在 Windows 版本 3.1 和更高版本中`TrackPopupMenu`,視窗在返回 之前不會接收WM_COMMAND消息。 在 Windows 3.0 中,`TrackPopupMenu`視窗在返回 之前接收WM_COMMAND消息。

*lpRect*<br/>
忽略。

### <a name="return-value"></a>傳回值

此方法返回在 Windows SDK 中調用[TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)的結果。

### <a name="remarks"></a>備註

浮動彈出式功能表可以出現在螢幕上的任意位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::追蹤彈出選單Ex

在指定位置顯示浮動彈出式功能表,並跟蹤彈出功能表上的項目選擇。

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>參數

*福旗*<br/>
為擴展功能表指定各種功能。 有關所有值及其含義的清單,請參閱[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

*X.*<br/>
指定彈出式功能表的螢幕座標中的水準位置。

*Y*<br/>
指定螢幕座標中螢幕座標中的垂直位置。

*pwnd*<br/>
指向具有彈出功能表並從創建的功能表接收消息的視窗的指標。 此視窗可以是目前應用程式的任何視窗,但不能為 NULL。 如果在*fuFlags*參數中指定TPM_NONOTIFY,則函數不會向*pWnd*發送任何消息。 函數必須返回*pWnd*指向的視窗才能接收WM_COMMAND消息。

*lptpm*<br/>
指向[TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams)結構的指標,該結構指定功能表不應重疊的螢幕區域。 此參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果在*fuFlags*參數中指定TPM_RETURNCMD,則返回值是使用者選擇的項的功能表項識別碼。 如果使用者取消功能表而不進行選擇,或者如果發生錯誤,則返回值為 0。

如果未在*fuFlags*參數中指定TPM_RETURNCMD,則如果函數成功,返回值為非零;如果函數失敗,則返回值為 0。 要取得延伸的錯誤資訊,請致電[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

浮動彈出式功能表可以出現在螢幕上的任意位置。 有關建立彈出式選單時處理錯誤的詳細資訊,請參閱[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
