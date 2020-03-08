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
ms.openlocfilehash: 1cd7be72dc6c9a38fae4f5ccc1a15c184a2d4466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855467"
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
|[CMenu：： CMenu](#cmenu)|建構 `CMenu` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|將新專案附加至此功能表的結尾。|
|[CMenu：： Attach](#attach)|將 Windows 功能表控制碼附加至 `CMenu` 物件。|
|[CMenu：： CheckMenuItem](#checkmenuitem)|在快顯功能表的功能表項目中，將核取記號放在旁邊或移除核取記號。|
|[CMenu：： CheckMenuRadioItem](#checkmenuradioitem)|在功能表項目旁邊放置一個選項按鈕，並移除群組中所有其他功能表項目的選項按鈕。|
|[CMenu：： CreateMenu](#createmenu)|建立空的功能表，並將它附加至 `CMenu` 物件。|
|[CMenu：： CreatePopupMenu](#createpopupmenu)|建立空的快顯功能表，並將其附加至 `CMenu` 物件。|
|[CMenu：:D eleteMenu](#deletemenu)|從功能表中刪除指定的專案。 如果功能表項目具有相關聯的快顯功能表，會將控制碼損毀到快顯功能表，並釋放它所使用的記憶體。|
|[CMenu：:D eleteTempMap](#deletetempmap)|刪除 `FromHandle` 成員函式所建立的任何暫存 `CMenu` 物件。|
|[CMenu：:D estroyMenu](#destroymenu)|終結附加至 `CMenu` 物件的功能表，並釋出功能表所佔用的任何記憶體。|
|[CMenu：:D etach](#detach)|從 `CMenu` 物件卸離 Windows 功能表控制碼，並傳回控制碼。|
|[CMenu：:D rawItem](#drawitem)|當主控描繪功能表的視覺外觀變更時由架構呼叫。|
|[CMenu：： EnableMenuItem](#enablemenuitem)|啟用、停用或變暗（灰色）功能表項目。|
|[CMenu：： FromHandle](#fromhandle)|傳回指定 Windows 功能表控制碼之 `CMenu` 物件的指標。|
|[CMenu：： GetDefaultItem](#getdefaultitem)|決定指定功能表上的預設功能表項目。|
|[CMenu：： GetMenuCoNtextHelpId](#getmenucontexthelpid)|抓取與功能表相關聯的說明內容識別碼。|
|[CMenu：： GetMenuInfo](#getmenuinfo)|抓取特定功能表上的資訊。|
|[CMenu：： GetMenuItemCount](#getmenuitemcount)|決定快顯視窗或最上層功能表中的專案數。|
|[CMenu：： GetMenuItemID](#getmenuitemid)|取得位於指定位置之功能表項目的功能表項目識別碼。|
|[CMenu：： GetMenuItemInfo](#getmenuiteminfo)|抓取功能表項目的相關資訊。|
|[CMenu：： GetMenuState](#getmenustate)|傳回指定之功能表項目的狀態，或快顯功能表中的專案數。|
|[CMenu：： GetMenuString](#getmenustring)|抓取指定功能表項目的標籤。|
|[CMenu：： GetSafeHmenu](#getsafehmenu)|傳回這個 `CMenu` 物件所包裝的 `m_hMenu`。|
|[CMenu：： GetSubMenu](#getsubmenu)|抓取快顯功能表的指標。|
|[CMenu::InsertMenu](#insertmenu)|在指定的位置插入新的功能表項目，將其他專案向下移動功能表。|
|[CMenu：： InsertMenuItem](#insertmenuitem)|在功能表中的指定位置插入新的功能表項目。|
|[CMenu：： LoadMenu](#loadmenu)|從可執行檔載入功能表資源，並將它附加至 `CMenu` 物件。|
|[CMenu：： LoadMenuIndirect](#loadmenuindirect)|從記憶體中的功能表範本載入功能表，並將其附加至 `CMenu` 物件。|
|[CMenu：： MeasureItem](#measureitem)|建立主控描繪功能表時，由架構呼叫以決定功能表尺寸。|
|[CMenu::ModifyMenu](#modifymenu)|變更指定位置的現有功能表項目。|
|[CMenu：： RemoveMenu](#removemenu)|從指定的功能表刪除具有相關聯快顯功能表的功能表項目。|
|[CMenu：： SetDefaultItem](#setdefaultitem)|設定指定功能表的預設功能表項目。|
|[CMenu：： SetMenuCoNtextHelpId](#setmenucontexthelpid)|設定要與功能表相關聯的說明內容識別碼。|
|[CMenu：： SetMenuInfo](#setmenuinfo)|設定特定功能表上的資訊。|
|[CMenu：： SetMenuItemBitmaps](#setmenuitembitmaps)|將指定的核取記號點陣圖與功能表項目產生關聯。|
|[CMenu：： SetMenuItemInfo](#setmenuiteminfo)|變更功能表項目的相關資訊。|
|[CMenu：： Trackpopupmenu 讓](#trackpopupmenu)|在指定的位置上顯示浮動快顯功能表，並追蹤快顯功能表上的專案選擇。|
|[CMenu：： TrackPopupMenuEx](#trackpopupmenuex)|在指定的位置上顯示浮動快顯功能表，並追蹤快顯功能表上的專案選擇。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMenu：： operator HMENU](#operator_hmenu)|抓取 menu 物件的控制碼。|
|[CMenu：： operator！ =](#operator_neq)|判斷兩個功能表物件是否不相等。|
|[CMenu：： operator = =](#operator_eq_eq)|判斷兩個功能表物件是否相等。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CMenu：： m_hMenu](#m_hmenu)|指定附加至 `CMenu` 物件之 Windows 功能表的控制碼。|

## <a name="remarks"></a>備註

它提供用來建立、追蹤、更新和終結功能表的成員函式。

在堆疊框架上建立 `CMenu` 物件做為本機，然後呼叫 `CMenu`的成員函式，視需要操作新的功能表。 接下來，呼叫[CWnd：： SetMenu](../../mfc/reference/cwnd-class.md#setmenu) ，將功能表設定為視窗，後面緊接著呼叫 `CMenu` 物件的[Detach](#detach)成員函式。 `CWnd::SetMenu` 成員函式會將視窗的功能表設定為 [新增] 功能表、重新繪製視窗以反映功能表變更，也會將功能表的擁有權傳遞至視窗。 `Detach` 的呼叫會從 `CMenu` 物件卸離 HMENU，如此一來，當本機 `CMenu` 變數超出範圍時，`CMenu` 物件的析構函式就不會嘗試摧毀不再擁有的功能表。 當視窗損毀時，功能表本身會自動終結。

您可以使用[LoadMenuIndirect](#loadmenuindirect)成員函式，從記憶體中的範本建立功能表，但藉由呼叫[LoadMenu](#loadmenu)而從資源建立的功能表更容易維護，而且功能表編輯器可以建立和修改功能表資源本身。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="appendmenu"></a>CMenu：： AppendMenu

將新專案附加至功能表的結尾。

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
指定將新功能表項目的狀態加入功能表中時的相關資訊。 其中包含 [備註] 區段中所列的一或多個值。

*nIDNewItem*<br/>
指定新功能表項目的命令識別碼，如果 [ *nFlags* ] 設定為 [MF_POPUP]，則為快顯功能表的功能表控制碼（`HMENU`）。 如果*nFlags*設為 MF_SEPARATOR，則會忽略*nIDNewItem*參數（不需要）。

*lpszNewItem*<br/>
指定新功能表項目的內容。 *NFlags*參數是用來以下列方式解讀*lpszNewItem* ：

|nFlags|LpszNewItem 的解讀|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含應用程式提供的32位值，應用程式可以用來維護與功能表項目相關聯的其他資料。 當應用程式處理 WM_MEASUREITEM 並 WM_DRAWITEM 訊息時，可使用這個32位值。 此值會儲存在與這些訊息一起提供之結構的 `itemData` 成員中。|
|MF_STRING|包含以 null 終止之字串的指標。 這是預設的轉譯。|
|MF_SEPARATOR|已忽略*lpszNewItem*參數（不需要）。|

*pBmp*<br/>
指向將用來做為功能表項目的 `CBitmap` 物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以藉由在*nFlags*中設定值來指定功能表項目的狀態。 當*nIDNewItem*指定快顯功能表時，它會成為附加的功能表的一部分。 如果該功能表已終結，則附加的功能表也會終結。 附加的功能表應該從 `CMenu` 物件卸離，以避免發生衝突。 請注意，MF_STRING 和 MF_OWNERDRAW 對 `AppendMenu`的點陣圖版本而言是不正確。

下列清單描述可在*nFlags*中設定的旗標：

- MF_CHECKED 會做為 MF_UNCHECKED 的切換，以將預設核取記號放在專案旁邊。 當應用程式提供核取記號點陣圖（請參閱[SetMenuItemBitmaps](#setmenuitembitmaps)成員函式）時，會顯示「核取記號開啟」點陣圖。

- MF_UNCHECKED 會做為 MF_CHECKED 的切換，以移除專案旁的核取記號。 當應用程式提供核取記號點陣圖（請參閱 `SetMenuItemBitmaps` 成員函式）時，會顯示「核取記號關閉」點陣圖。

- MF_DISABLED 停用功能表項目，使其無法選取，但不會變暗。

- MF_ENABLED 啟用功能表項目，讓它可以選取並從其暗灰色狀態還原。

- MF_GRAYED 停用功能表項目，使其無法選取且變暗。

- MF_MENUBARBREAK 會將專案放在靜態功能表的新行或快顯功能表的新欄中。 新的快顯功能表欄將會與舊的資料行分隔。

- MF_MENUBREAK 會將專案放在靜態功能表的新行或快顯功能表的新欄中。 不會在資料行之間放置分隔線。

- MF_OWNERDRAW 指定專案為主控描繪專案。 當第一次顯示功能表時，擁有功能表的視窗會收到 WM_MEASUREITEM 訊息，其會抓取功能表項目的高度和寬度。 當擁有者必須更新功能表項目的視覺外觀時，就會傳送 WM_DRAWITEM 訊息。 最上層功能表項目的這個選項無效。

- MF_POPUP 指定功能表項目具有與它相關聯的快顯功能表。 ID 參數會指定要與專案相關聯之快顯功能表的控制碼。 這是用來將最上層快顯功能表或階層式快顯功能表加入快顯功能表專案。

- MF_SEPARATOR 繪製水準分隔線。 只能在快顯功能表中使用。 這一行不可為灰色、已停用或反白顯示。 會忽略其他參數。

- MF_STRING 指定功能表項目是字元字串。

下列每個群組都會列出互斥的旗標，而且不能同時使用：

- MF_DISABLED、MF_ENABLED 和 MF_GRAYED

- MF_STRING、MF_OWNERDRAW、MF_SEPARATOR 和點陣圖版本

- MF_MENUBARBREAK 和 MF_MENUBREAK

- MF_CHECKED 和 MF_UNCHECKED

每當位於視窗中的功能表變更時（不論是否顯示視窗），應用程式應該呼叫[CWnd：:D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>範例

  請參閱[CMenu：： CreateMenu](#createmenu)的範例。

##  <a name="attach"></a>CMenu：： Attach

將現有的 Windows 功能表附加至 `CMenu` 物件。

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
指定 Windows 功能表的控制碼。

### <a name="return-value"></a>傳回值

如果作業成功，則為非零;否則為0。

### <a name="remarks"></a>備註

如果已將功能表附加至 `CMenu` 物件，則不應呼叫此函式。 功能表控制碼會儲存在 `m_hMenu` 資料成員中。

如果您要操作的功能表已經與某個視窗相關聯，您可以使用[CWnd：： GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函式來取得功能表的控制碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>CMenu：： CheckMenuItem

在快顯功能表中，將核取記號新增至功能表項目或從中移除核取記號。

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>參數

*nIDCheckItem*<br/>
指定要檢查的功能表項目（由*nCheck*決定）。

*nCheck*<br/>
指定如何檢查功能表項目，以及如何判斷專案在功能表中的位置。 *NCheck*參數可以是 MF_CHECKED 或 MF_UNCHECKED 與 MF_BYPOSITION 或 MF_BYCOMMAND 旗標的組合。 這些旗標可以使用位 OR 運算子結合。 它們具有下列意義：

- MF_BYCOMMAND 指定參數提供現有功能表項目的命令識別碼。 這是預設值。

- MF_BYPOSITION 指定參數提供現有功能表項目的位置。 第一個專案位於位置0。

- MF_CHECKED 會做為 MF_UNCHECKED 的切換，以將預設核取記號放在專案旁邊。

- MF_UNCHECKED 會做為 MF_CHECKED 的切換，以移除專案旁的核取記號。

### <a name="return-value"></a>傳回值

專案的先前狀態： MF_CHECKED 或 MF_UNCHECKED，如果功能表項目不存在，則為0xFFFFFFFF。

### <a name="remarks"></a>備註

*NIDCheckItem*參數會指定要修改的專案。

*NIDCheckItem*參數可以識別快顯功能表專案和功能表項目。 不需要執行任何特殊步驟，就能檢查快顯功能表專案。 無法檢查最上層功能表項目。 快顯功能表專案必須依位置檢查，因為它沒有相關聯的功能表項目識別碼。

### <a name="example"></a>範例

  請參閱[CMenu：： GetMenuState](#getmenustate)的範例。

##  <a name="checkmenuradioitem"></a>CMenu：： CheckMenuRadioItem

檢查指定的功能表項目，並使它成為一個選項按鈕。

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*nIDFirst*<br/>
指定（做為識別碼或位移，視*nFlags*的值而定），也就是選項按鈕群組中的第一個功能表項目。

*nIDLast*<br/>
指定（做為識別碼或位移，視*nFlags*的值而定），也就是選項按鈕群組中的最後一個功能表項目。

*nIDItem*<br/>
指定（做為識別碼或位移，視*nFlags*的值而定），群組中的專案將會以選項按鈕進行檢查。

*nFlags*<br/>
以下列方式指定*nIDFirst*、 *nIDLast*和*nIDItem*的轉譯：

|nFlags|解讀|
|------------|--------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。|

### <a name="return-value"></a>傳回值

如果成功，則為非零;否則為0

### <a name="remarks"></a>備註

同時，函式會取消核取相關聯群組中的所有其他功能表項目，並清除這些專案的 [廣播] 專案類型旗標。 核取的專案是使用選項按鈕（或專案符號）點陣圖而非核取記號點陣圖來顯示。

### <a name="example"></a>範例

  請參閱[ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)的範例。

##  <a name="cmenu"></a>CMenu：： CMenu

建立空的功能表，並將它附加至 `CMenu` 物件。

```
CMenu();
```

### <a name="remarks"></a>備註

在您呼叫 `CMenu:` 的其中一個 create 或 load 成員函式之前，不會建立此功能表。

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [附加](#attach)

##  <a name="createmenu"></a>CMenu：： CreateMenu

建立功能表，並將其附加至 `CMenu` 物件。

```
BOOL CreateMenu();
```

### <a name="return-value"></a>傳回值

如果已成功建立功能表，則為非零;否則為0。

### <a name="remarks"></a>備註

此功能表一開始是空的。 您可以使用 `AppendMenu` 或 `InsertMenu` 成員函式來新增功能表項目。

如果將功能表指派給視窗，則會在終結視窗時自動終結。

在結束之前，如果功能表未指派給視窗，應用程式必須釋放與功能表相關聯的系統資源。 應用程式會藉由呼叫[DestroyMenu](#destroymenu)成員函式來釋放功能表。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>CMenu：： CreatePopupMenu

建立快顯功能表，並將其附加至 `CMenu` 物件。

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>傳回值

如果成功建立快顯功能表，則為非零;否則為0。

### <a name="remarks"></a>備註

此功能表一開始是空的。 您可以使用 `AppendMenu` 或 `InsertMenu` 成員函式來新增功能表項目。 應用程式可以將快顯功能表加入至現有的功能表或快顯功能表。 `TrackPopupMenu` 成員函式可以用來將此功能表顯示為浮動快顯功能表，以及追蹤快顯功能表上的選取專案。

如果將功能表指派給視窗，則會在終結視窗時自動終結。 如果將功能表加入至現有的功能表，則會在該功能表終結時自動終結。

在結束之前，應用程式必須釋放與快顯功能表相關聯的系統資源（如果未將功能表指派給視窗）。 應用程式會藉由呼叫[DestroyMenu](#destroymenu)成員函式來釋放功能表。

### <a name="example"></a>範例

  請參閱[CMenu：： CreateMenu](#createmenu)的範例。

##  <a name="deletemenu"></a>CMenu：:D eleteMenu

從功能表中刪除專案。

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*nPosition*<br/>
指定要刪除的功能表項目（由*nFlags*決定）。

*nFlags*<br/>
是用來以下列方式解讀*nPosition* ：

|nFlags|NPosition 的解讀|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。|

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

如果功能表項目具有相關聯的快顯功能表，`DeleteMenu` 會終結快顯功能表的控制碼，並釋出快顯功能表所使用的記憶體。

每當位於視窗中的功能表變更時（不論是否顯示視窗），應用程式都必須呼叫[CWnd：:D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>範例

  請參閱[CWnd：： GetMenu](../../mfc/reference/cwnd-class.md#getmenu)的範例。

##  <a name="deletetempmap"></a>CMenu：:D eleteTempMap

由 `CWinApp` 閒置時間處理常式自動呼叫，會刪除[FromHandle](#fromhandle)成員函式所建立的任何暫存 `CMenu` 物件。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>備註

`DeleteTempMap` 在刪除 `CMenu` 物件之前，先卸離附加至暫存 `CMenu` 物件的 Windows 功能表物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>CMenu：:D estroyMenu

損毀功能表和使用的任何 Windows 資源。

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>傳回值

如果功能表已終結，則為非零;否則為0。

### <a name="remarks"></a>備註

功能表在終結之前，會從 `CMenu` 物件卸離。 系統會在 `CMenu` 的析構函式中自動呼叫 Windows `DestroyMenu` 函數。

### <a name="example"></a>範例

  請參閱[CMenu：： CreateMenu](#createmenu)的範例。

##  <a name="detach"></a>CMenu：:D etach

從 `CMenu` 物件卸離 Windows 功能表，並傳回控制碼。

```
HMENU Detach();
```

### <a name="return-value"></a>傳回值

HMENU 類型的控制碼，如果成功，則為 Windows 功能表否則為 Null。

### <a name="remarks"></a>備註

`m_hMenu` 的資料成員會設定為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>CMenu：:D rawItem

當主控描繪功能表的視覺外觀變更時由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標，其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT` 結構的 `itemAction` 成員會定義要執行的繪圖動作。 覆寫這個成員函式，以針對主控描繪 `CMenu` 物件來執行繪製。 在此成員函式終止之前，應用程式應該還原針對*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面（GDI）物件。

如需 `DRAWITEMSTRUCT` 結構的說明，請參閱[CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 。

### <a name="example"></a>範例

下列程式碼來自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)範例：

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>CMenu：： EnableMenuItem

啟用、停用或變暗功能表項目。

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>參數

*nIDEnableItem*<br/>
指定要啟用的功能表項目（由*nEnable*決定）。 這個參數可以指定快顯功能表專案和標準功能表項目。

*nEnable*<br/>
指定要採取的動作。 它可以是 MF_DISABLED、MF_ENABLED 或 MF_GRAYED 的組合，以及 MF_BYCOMMAND 或 MF_BYPOSITION。 這些值可以使用位 OR 運算子結合。 這些值具有以下意義：

- MF_BYCOMMAND 指定參數提供現有功能表項目的命令識別碼。 這是預設值。

- MF_BYPOSITION 指定參數提供現有功能表項目的位置。 第一個專案位於位置0。

- MF_DISABLED 停用功能表項目，使其無法選取，但不會變暗。

- MF_ENABLED 啟用功能表項目，讓它可以選取並從其暗灰色狀態還原。

- MF_GRAYED 停用功能表項目，使其無法選取且變暗。

### <a name="return-value"></a>傳回值

先前的狀態（MF_DISABLED、MF_ENABLED 或 MF_GRAYED）或-1 （如果無效）。

### <a name="remarks"></a>備註

[CreateMenu](#createmenu)、 [InsertMenu](#insertmenu)、 [ModifyMenu](#modifymenu)和[LoadMenuIndirect](#loadmenuindirect)成員函式也可以設定功能表項目的狀態（已啟用、已停用或暗灰色）。

若要使用 MF_BYPOSITION 值，應用程式必須使用正確的 `CMenu`。 如果使用功能表列的 `CMenu`，則最上層功能表項目（功能表列中的專案）會受到影響。 若要依位置設定快捷方式或嵌套快顯功能表中的專案狀態，應用程式必須指定快顯功能表的 [`CMenu`]。

當應用程式指定 MF_BYCOMMAND 旗標時，Windows 會檢查所有屬於 `CMenu`的快顯功能表項;因此，除非出現重複的功能表項目，否則使用功能表列的 `CMenu` 就已足夠。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>CMenu：： FromHandle

傳回指定功能表的 Windows 控制碼之 `CMenu` 物件的指標。

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
功能表的 Windows 控制碼。

### <a name="return-value"></a>傳回值

可能是暫時或永久之 `CMenu` 的指標。

### <a name="remarks"></a>備註

如果 `CMenu` 物件尚未附加至 Windows menu 物件，則會建立並附加暫存 `CMenu` 物件。

只有在下一次應用程式的事件迴圈中有閒置時間時，才會將此暫存 `CMenu` 物件有效，此時所有暫存物件都會遭到刪除。

### <a name="example"></a>範例

  請參閱[CMenu：： CreateMenu](#createmenu)的範例。

##  <a name="getdefaultitem"></a>CMenu：： GetDefaultItem

決定指定功能表上的預設功能表項目。

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*gmdiFlags*<br/>
值，指定函數搜尋功能表項目的方式。 這個參數可以是 none、one 或下列值的組合：

|值|意義|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|指定如果預設專案是開啟子功能表的專案，則函式會以遞迴方式在對應的子功能表中進行搜尋。 如果子功能表沒有預設專案，則傳回值會識別開啟子功能表的專案。<br /><br /> 根據預設，函式會傳回指定功能表上的第一個預設專案，而不論其是否為開啟子功能表的專案。|
|GMDI_USEDISABLED|指定函數要傳回預設專案，即使已停用。<br /><br /> 根據預設，函式會略過停用或呈現灰色的專案。|

*fByPos*<br/>
值，指定是否要取出功能表項目的識別碼或其位置。 如果此參數為 FALSE，則會傳回識別碼。 否則，會傳回位置。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值是功能表項目的識別碼或位置。 如果函式失敗，則傳回值為-1。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 函數[GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="getmenucontexthelpid"></a>CMenu：： GetMenuCoNtextHelpId

抓取與 `CMenu`相關聯的內容說明識別碼。

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>傳回值

目前與 `CMenu` 相關聯的內容說明識別碼（如果有的話）。否則為零。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="getmenuinfo"></a>CMenu：： GetMenuInfo

抓取功能表的資訊。

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>參數

*lpcmi*<br/>
包含功能表資訊之[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)結構的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零;否則，傳回值為零。

### <a name="remarks"></a>備註

呼叫此函式可取得功能表的相關資訊。

##  <a name="getmenuitemcount"></a>CMenu：： GetMenuItemCount

決定快顯視窗或最上層功能表中的專案數。

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>傳回值

如果函式成功，則為功能表中的專案數;否則為-1。

### <a name="example"></a>範例

  請參閱[CWnd：： GetMenu](../../mfc/reference/cwnd-class.md#getmenu)的範例。

##  <a name="getmenuitemid"></a>CMenu：： GetMenuItemID

取得功能表項目的功能表項目識別碼，此專案位於*nPos*所定義的位置。

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定正在抓取其識別碼之功能表項目的位置（以零為基底）。

### <a name="return-value"></a>傳回值

如果函式成功，則為快顯功能表中指定專案的專案識別碼。 如果指定的專案是快顯功能表（而不是快顯功能表中的專案），則傳回值為-1。 如果*nPos*對應至 [分隔符號] 功能表項目，則傳回值為0。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="getmenuiteminfo"></a>CMenu：： GetMenuItemInfo

抓取功能表項目的相關資訊。

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
要取得相關資訊之功能表項目的識別碼或位置。 這個參數的意義取決於 `ByPos`的值。

*lpMenuItemInfo*<br/>
如 Windows SDK 中所述的[MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow)指標，其中包含功能表的相關資訊。

*fByPos*<br/>
值，指定 `nIDItem`的意義。 根據預設，`ByPos` 為 FALSE，表示 uItem 是功能表項目識別碼。 如果 `ByPos` 未設定為 FALSE，則表示功能表項目位置。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。 如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請使用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)，如 Windows SDK 中所述。

### <a name="remarks"></a>備註

此成員函式會實作用 Win32 函式[GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)的行為，如 Windows SDK 中所述。 請注意，在 `GetMenuItemInfo`的 MFC 執行中，您不會使用功能表的控制碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>CMenu：： GetMenuState

傳回指定之功能表項目的狀態，或快顯功能表中的專案數。

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>參數

*nID*<br/>
指定*nFlags*所決定的功能表項目識別碼。

*nFlags*<br/>
指定*nID*的本質。 它可能是下列其中一個值：

- MF_BYCOMMAND 指定參數提供現有功能表項目的命令識別碼。 這是預設值。

- MF_BYPOSITION 指定參數提供現有功能表項目的位置。 第一個專案位於位置0。

### <a name="return-value"></a>傳回值

如果指定的專案不存在，則值0xFFFFFFFF。 如果*nId*識別快顯功能表，則高序位位元組包含快顯功能表中的專案數，而低序位位元組則包含與快顯功能表相關聯的功能表旗標。 否則，傳回值是下列清單中值的遮罩（布林值或）（此遮罩描述*nId*識別的功能表項目狀態）：

- MF_CHECKED 會做為 MF_UNCHECKED 的切換，以將預設核取記號放在專案旁邊。 當應用程式提供核取記號點陣圖（請參閱 `SetMenuItemBitmaps` 成員函式）時，會顯示「核取記號開啟」點陣圖。

- MF_DISABLED 停用功能表項目，使其無法選取，但不會變暗。

- MF_ENABLED 啟用功能表項目，讓它可以選取並從其暗灰色狀態還原。 請注意，這個常數的值是 0;使用此值時，應用程式不應該針對失敗進行測試。

- MF_GRAYED 停用功能表項目，使其無法選取且變暗。

- MF_MENUBARBREAK 會將專案放在靜態功能表的新行或快顯功能表的新欄中。 新的快顯功能表欄將會與舊的資料行分隔。

- MF_MENUBREAK 會將專案放在靜態功能表的新行或快顯功能表的新欄中。 不會在資料行之間放置分隔線。

- MF_SEPARATOR 繪製水準分隔線。 只能在快顯功能表中使用。 這一行不可為灰色、已停用或反白顯示。 會忽略其他參數。

- MF_UNCHECKED 會做為 MF_CHECKED 的切換，以移除專案旁的核取記號。 當應用程式提供核取記號點陣圖（請參閱 `SetMenuItemBitmaps` 成員函式）時，會顯示「核取記號關閉」點陣圖。 請注意，這個常數的值是 0;使用此值時，應用程式不應該針對失敗進行測試。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>CMenu：： GetMenuString

將指定功能表項目的標籤複製到指定的緩衝區。

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
指定功能表項目的整數識別碼，或功能表中功能表項目的位移（視*nFlags*的值而定）。

*lpString*<br/>
指向要接收標籤的緩衝區。

*rString*<br/>
`CString` 物件的參考，它會接收已複製的功能表字串。

*nMaxCount*<br/>
指定要複製之標籤的最大長度（以字元為單位）。 如果標籤的長度超過*nMaxCount*中指定的最大值，則會截斷額外的字元。

*nFlags*<br/>
指定*nIDItem*參數的轉譯。 它可能是下列其中一個值：

|nFlags|NIDItem 的解讀|
|------------|-------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。|

### <a name="return-value"></a>傳回值

指定複製到緩衝區的實際字元數，不包括 null 結束字元。

### <a name="remarks"></a>備註

*NMaxCount*參數應大於標籤中的字元數，以容納終止字串的 null 字元。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="getsafehmenu"></a>CMenu：： GetSafeHmenu

傳回此 `CMenu` 物件所包裝的 HMENU，或 Null`CMenu` 指標。

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>範例

  請參閱[CMenu：： LoadMenu](#loadmenu)的範例。

##  <a name="getsubmenu"></a>CMenu：： GetSubMenu

抓取快顯功能表的 `CMenu` 物件。

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定功能表中所包含快顯功能表的位置。 第一個功能表項目的位置值從0開始。 快顯功能表的識別碼不能用在此函式中。

### <a name="return-value"></a>傳回值

`CMenu` 物件的指標，其 `m_hMenu` 成員在指定的位置有快顯功能表時，包含快顯功能表的控制碼;否則為 Null。 如果 `CMenu` 物件不存在，則會建立一個暫存的物件。 不應儲存傳回的 `CMenu` 指標。

### <a name="example"></a>範例

  請參閱[CMenu：： trackpopupmenu 讓](#trackpopupmenu)的範例。

##  <a name="insertmenu"></a>CMenu：： InsertMenu

在*nPosition*指定的位置插入新的功能表項目，並將其他專案向下移動功能表。

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

*nPosition*<br/>
指定要在其中插入新功能表項目的功能表項目。 *NFlags*參數可透過下列方式用來解讀*nPosition* ：

|nFlags|NPosition 的解讀|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。 如果*nPosition*為-1，則新的功能表項目會附加至功能表的結尾。|

*nFlags*<br/>
指定如何解讀*nPosition* ，並指定將新功能表項目的狀態加入功能表中時的相關資訊。 如需可能設定的旗標清單，請參閱[AppendMenu](#appendmenu)成員函式。 若要指定一個以上的值，請使用位 OR 運算子，將它們與 MF_BYCOMMAND 或 MF_BYPOSITION 旗標結合。

*nIDNewItem*<br/>
指定新功能表項目的命令識別碼，如果 [ *nFlags* ] 設定為 [MF_POPUP]，則為快顯功能表的功能表控制碼（HMENU）。 如果*nFlags*設為 MF_SEPARATOR，則會忽略*nIDNewItem*參數（不需要）。

*lpszNewItem*<br/>
指定新功能表項目的內容。 *nFlags*可透過下列方式用來解讀*lpszNewItem* ：

|nFlags|LpszNewItem 的解讀|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含應用程式提供的32位值，應用程式可以用來維護與功能表項目相關聯的其他資料。 這個32位值可供[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)和[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)訊息所提供之結構的 `itemData` 成員中的應用程式使用。 當功能表項目一開始顯示或變更時，就會傳送這些訊息。|
|MF_STRING|包含以 null 終止之字串的長指標。 這是預設的轉譯。|
|MF_SEPARATOR|已忽略*lpszNewItem*參數（不需要）。|

*pBmp*<br/>
指向將用來做為功能表項目的 `CBitmap` 物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式可以藉由在*nFlags*中設定值來指定功能表項目的狀態。

每當位於視窗中的功能表變更時（不論是否顯示視窗），應用程式應該呼叫 `CWnd::DrawMenuBar`。

當*nIDNewItem*指定快顯功能表時，它會成為其插入所在功能表的一部分。 如果該功能表已終結，則插入的功能表也會終結。 插入的功能表應該從 `CMenu` 物件卸離，以避免發生衝突。

如果使用中的多重文件介面（MDI）子視窗最大化，而應用程式藉由呼叫此函式並指定 MF_BYPOSITION 旗標，將快顯功能表插入 MDI 應用程式的功能表中，則功能表會插入一個位置，遠超過預期. 發生這種情況的原因是，現用 MDI 子視窗的 [控制] 功能表會插入至 MDI 框架視窗功能表列的第一個位置。 若要適當地放置功能表，應用程式必須將1新增至要使用的位置值。 應用程式可以使用 WM_MDIGETACTIVE 訊息來判斷目前作用中的子視窗是否最大化。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>CMenu：： InsertMenuItem

在功能表中的指定位置插入新的功能表項目。

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
請參閱 Windows SDK [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)中的*uItem*說明。

*lpMenuItemInfo*<br/>
請參閱 Windows SDK `InsertMenuItem` 中的*lpmii*描述。

*fByPos*<br/>
請參閱 Windows SDK `InsertMenuItem` 中的*fByPosition*描述。

### <a name="remarks"></a>備註

此函式會包裝[InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)，如 Windows SDK 中所述。

##  <a name="loadmenu"></a>CMenu：： LoadMenu

從應用程式的可執行檔載入功能表資源，並將它附加至 `CMenu` 物件。

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
指向以 null 終止的字串，其中包含要載入的功能表資源名稱。

*nIDResource*<br/>
指定要載入之功能表資源的功能表識別碼。

### <a name="return-value"></a>傳回值

如果已成功載入功能表資源，則為非零;否則為0。

### <a name="remarks"></a>備註

在結束之前，如果功能表未指派給視窗，應用程式必須釋放與功能表相關聯的系統資源。 應用程式會藉由呼叫[DestroyMenu](#destroymenu)成員函式來釋放功能表。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>CMenu：： LoadMenuIndirect

從記憶體中的功能表範本載入資源，並將它附加至 `CMenu` 物件。

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>參數

*lpMenuTemplate*<br/>
指向功能表範本（這是單一[MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader)結構和一或多個[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)結構的集合）。 如需這兩個結構的詳細資訊，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

如果已成功載入功能表資源，則為非零;否則為0。

### <a name="remarks"></a>備註

功能表範本是標頭，後面接著一個或多個[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)結構的集合，其中每一個都可能包含一或多個功能表項目和快顯功能表。

版本號碼應為0。

`mtOption` 旗標應該包含快顯清單中最後一個專案的 MF_END，以及主要清單中的最後一個專案。 如需其他旗標，請參閱 `AppendMenu` 成員函式。 當 `mtOption`中指定 MF_POPUP 時，必須從 MENUITEMTEMPLATE 結構中省略 `mtId` 成員。

配置給 MENUITEMTEMPLATE 結構的空間必須夠大，才能 `mtString` 將功能表項目的名稱包含為以 null 結束的字串。

在結束之前，如果功能表未指派給視窗，應用程式必須釋放與功能表相關聯的系統資源。 應用程式會藉由呼叫[DestroyMenu](#destroymenu)成員函式來釋放功能表。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>CMenu：： m_hMenu

指定附加至 `CMenu` 物件之 Windows 功能表的 HMENU 控制碼。

```
HMENU m_hMenu;
```

### <a name="example"></a>範例

  請參閱[CMenu：： LoadMenu](#loadmenu)的範例。

##  <a name="measureitem"></a>CMenu：： MeasureItem

建立具有擁有者繪製樣式的功能表時，由架構呼叫。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lpMeasureItemStruct*<br/>
`MEASUREITEMSTRUCT` 結構的指標。

### <a name="remarks"></a>備註

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式並填入 `MEASUREITEMSTRUCT` 結構，以通知視窗的功能表大小。

如需 `MEASUREITEMSTRUCT` 結構的說明，請參閱[CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 。

### <a name="example"></a>範例

下列程式碼來自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)範例：

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>CMenu：： ModifyMenu

在*nPosition*指定的位置變更現有的功能表項目。

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

*nPosition*<br/>
指定要變更的功能表項目。 *NFlags*參數可透過下列方式用來解讀*nPosition* ：

|nFlags|NPosition 的解讀|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。|

*nFlags*<br/>
指定如何解讀*nPosition* ，並提供對功能表項目所做之變更的相關資訊。 如需可設定的旗標清單，請參閱[AppendMenu](#appendmenu)成員函式。

*nIDNewItem*<br/>
指定已修改功能表項目的命令識別碼，如果*nFlags*設定為 MF_POPUP，則為快顯功能表的功能表控制碼（HMENU）。 如果*nFlags*設為 MF_SEPARATOR，則會忽略*nIDNewItem*參數（不需要）。

*lpszNewItem*<br/>
指定新功能表項目的內容。 *NFlags*參數可透過下列方式用來解讀*lpszNewItem* ：

|nFlags|LpszNewItem 的解讀|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含應用程式提供的32位值，應用程式可以用來維護與功能表項目相關聯的其他資料。 當應用程式處理 MF_MEASUREITEM 並 MF_DRAWITEM 時，可以使用這個32位值。|
|MF_STRING|包含以 null 結束之字串或 `CString`的長指標。|
|MF_SEPARATOR|已忽略*lpszNewItem*參數（不需要）。|

*pBmp*<br/>
指向將用來做為功能表項目的 `CBitmap` 物件。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

應用程式會藉由設定*nFlags*中的值，來指定功能表項目的新狀態。 如果此函式取代與功能表項目相關聯的快顯功能表，它會終結舊的快顯功能表，並釋出快顯功能表所使用的記憶體。

當*nIDNewItem*指定快顯功能表時，它會成為其插入所在功能表的一部分。 如果該功能表已終結，則插入的功能表也會終結。 插入的功能表應該從 `CMenu` 物件卸離，以避免發生衝突。

每當位於視窗中的功能表變更時（不論是否顯示視窗），應用程式應該呼叫 `CWnd::DrawMenuBar`。 若要變更現有功能表項目的屬性，使用 `CheckMenuItem` 和 `EnableMenuItem` 成員函式的速度會更快。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="operator_hmenu"></a>CMenu：： operator HMENU

使用這個運算子來取出 `CMenu` 物件的控制碼。

```
operator HMENU() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為 `CMenu` 物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

您可以使用控制碼直接呼叫 Windows Api。

##  <a name="operator_neq"></a>CMenu：： operator！ =

判斷兩個功能表在邏輯上是否不相等。

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>參數

*下拉式功能表*<br/>
要比較的 `CMenu` 物件。

### <a name="remarks"></a>備註

測試左側的功能表物件是否不等於右邊的功能表物件。

##  <a name="operator_eq_eq"></a>CMenu：： operator = =

判斷兩個功能表在邏輯上是否相等。

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>參數

*下拉式功能表*<br/>
要比較的 `CMenu` 物件。

### <a name="remarks"></a>備註

測試左邊的功能表物件是否等於右邊的 menu 物件（以 HMENU 值為依據）。

##  <a name="removemenu"></a>CMenu：： RemoveMenu

從功能表中刪除具有相關聯快顯功能表的功能表項目。

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*nPosition*<br/>
指定要移除的功能表項目。 *NFlags*參數可透過下列方式用來解讀*nPosition* ：

|nFlags|NPosition 的解讀|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。|

*nFlags*<br/>
指定如何解讀*nPosition* 。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

它不會損毀快顯功能表的控制碼，因此可以重複使用功能表。 在呼叫此函式之前，應用程式可能會呼叫 `GetSubMenu` 成員函式來抓取快顯 `CMenu` 物件以供重複使用。

每當位於視窗中的功能表變更時（不論是否顯示視窗），應用程式都必須呼叫 `CWnd::DrawMenuBar`。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="setdefaultitem"></a>CMenu：： SetDefaultItem

設定指定功能表的預設功能表項目。

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
新預設功能表項目的識別碼或位置，或-1 表示沒有預設專案。 這個參數的意義取決於*fByPos*的值。

*fByPos*<br/>
指定*uItem*意義的值。 如果此參數為 FALSE，則*uItem*是功能表項目識別碼。 否則，它是功能表項目位置。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。 如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請使用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)，如 Windows SDK 中所述。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 函數[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="setmenucontexthelpid"></a>CMenu：： SetMenuCoNtextHelpId

將內容說明識別碼與 `CMenu`產生關聯。

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>參數

*dwCoNtextHelpId*<br/>
要與 `CMenu`相關聯的內容說明識別碼。

### <a name="return-value"></a>傳回值

如果成功，則為非零;否則為0

### <a name="remarks"></a>備註

功能表中的所有專案都會共用此識別碼，因此無法將說明內容識別碼附加至個別的功能表項目。

### <a name="example"></a>範例

  請參閱[CMenu：： InsertMenu](#insertmenu)的範例。

##  <a name="setmenuinfo"></a>CMenu：： SetMenuInfo

設定功能表的資訊。

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>參數

*lpcmi*<br/>
包含功能表資訊之[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)結構的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零;否則，傳回值為零。

### <a name="remarks"></a>備註

呼叫此函式可設定功能表的特定資訊。

##  <a name="setmenuitembitmaps"></a>CMenu：： SetMenuItemBitmaps

將指定的點陣圖與功能表項目產生關聯。

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>參數

*nPosition*<br/>
指定要變更的功能表項目。 *NFlags*參數可透過下列方式用來解讀*nPosition* ：

|nFlags|NPosition 的解讀|
|------------|---------------------------------|
|MF_BYCOMMAND|指定參數提供現有功能表項目的命令識別碼。 如果 MF_BYCOMMAND 或 MF_BYPOSITION 皆未設定，則這是預設值。|
|MF_BYPOSITION|指定參數提供現有功能表項目的位置。 第一個專案位於位置0。|

*nFlags*<br/>
指定如何解讀*nPosition* 。

*pBmpUnchecked*<br/>
指定要用於未核取之功能表項目的點陣圖。

*pBmpChecked*<br/>
指定要用於已檢查功能表項目的點陣圖。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

無論是否核取或取消選取功能表項目，Windows 都會在功能表項目旁邊顯示適當的點陣圖。

如果*pBmpUnchecked*或*pBmpChecked*是 Null，則 Windows 不會在對應屬性的功能表項目旁邊顯示任何內容。 如果兩個參數都是 Null，則 Windows 會在檢查項目時使用預設的核取記號，並在取消核取專案時移除核取記號。

當功能表被終結時，這些點陣圖並不會損毀;應用程式必須摧毀它們。

Windows `GetMenuCheckMarkDimensions` 函式會抓取用於功能表項目之預設核取記號的維度。 應用程式會使用這些值來判斷此函式所提供之點陣圖的適當大小。 取得大小、建立您的點陣圖，然後加以設定。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>CMenu：： SetMenuItemInfo

變更功能表項目的相關資訊。

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>參數

*uItem*<br/>
請參閱 Windows SDK [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)中的*uItem*說明。

*lpMenuItemInfo*<br/>
請參閱 Windows SDK `SetMenuItemInfo` 中的*lpmii*描述。

*fByPos*<br/>
請參閱 Windows SDK `SetMenuItemInfo` 中的*fByPosition*描述。

### <a name="remarks"></a>備註

此函式會包裝[SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)，如 Windows SDK 中所述。

##  <a name="trackpopupmenu"></a>CMenu：： Trackpopupmenu 讓

在指定的位置上顯示浮動快顯功能表，並追蹤快顯功能表上的專案選擇。

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
指定螢幕位置和滑鼠位置旗標。 如需可用旗標的清單，請參閱[trackpopupmenu 讓](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)。

*x*<br/>
指定快顯功能表之螢幕座標中的水準位置。 視*nFlags*參數的值而定，功能表可以靠左對齊、靠右對齊或置中相對於此位置的中心。

*y*<br/>
指定螢幕上功能表頂端螢幕座標的垂直位置。

*pWnd*<br/>
識別擁有快顯功能表的視窗。 即使指定了 TPM_NONOTIFY 旗標，這個參數也不可以是 Null。 此視窗會接收來自功能表的所有 WM_COMMAND 訊息。 在 Windows 版本3.1 和更新版本中，除非 `TrackPopupMenu` 傳回，否則視窗不會收到 WM_COMMAND 訊息。 在 Windows 3.0 中，視窗會在 `TrackPopupMenu` 傳回之前收到 WM_COMMAND 訊息。

*lpRect*<br/>
忽略：

### <a name="return-value"></a>傳回值

這個方法會傳回 Windows SDK 中呼叫[trackpopupmenu 讓](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)的結果。

### <a name="remarks"></a>備註

浮動快顯功能表可能會出現在畫面上的任何位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>CMenu：： TrackPopupMenuEx

在指定的位置上顯示浮動快顯功能表，並追蹤快顯功能表上的專案選擇。

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>參數

*fuFlags*<br/>
指定擴充功能表的各種功能。 如需所有值及其意義的清單，請參閱[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

*x*<br/>
指定快顯功能表之螢幕座標中的水準位置。

*y*<br/>
指定螢幕上功能表頂端螢幕座標的垂直位置。

*pWnd*<br/>
擁有快顯功能表並從 [已建立] 功能表接收訊息之視窗的指標。 這個視窗可以是目前應用程式的任何視窗，但不能是 Null。 如果您在*fuFlags*參數中指定 TPM_NONOTIFY，此函式不會傳送任何訊息至*pWnd*。 函式必須針對*pWnd*所指向的視窗傳回，以接收 WM_COMMAND 訊息。

*lptpm*<br/>
[TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams)結構的指標，指定功能表不應重迭的螢幕區域。 這個參數可以是 Null。

### <a name="return-value"></a>傳回值

如果您在*fuFlags*參數中指定 TPM_RETURNCMD，則傳回值會是使用者選取之專案的功能表項目識別碼。 如果使用者取消功能表而未進行選取，或發生錯誤，則傳回值為0。

如果您未在*fuFlags*參數中指定 TPM_RETURNCMD，如果函式成功，則傳回值為非零，如果失敗，則傳回0。 若要取得延伸錯誤資訊，請呼叫[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

浮動快顯功能表可能會出現在畫面上的任何位置。 如需有關在建立快顯功能表時處理錯誤的詳細資訊，請參閱[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
