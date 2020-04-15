---
title: CMDIFrameWnd 類別
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: a6e68f6368a7b45e0a566a7d2d12f23a9cd62b12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370051"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd 類別

提供 Windows 多重文件介面 (MDI) 框架視窗的功能，以及管理視窗的成員。

## <a name="syntax"></a>語法

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMDIFramewnd::CMDIFramewnd](#cmdiframewnd)|建構 `CMDIFrameWnd`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDIFramewnd::創建用戶端](#createclient)|為此`CMDIFrameWnd`創建一個 Windows MDICLIENT 視窗。 由的成員`OnCreate`函數呼`CWnd`叫 。|
|[CMDIFramewnd::創建新兒童](#createnewchild)|創建新的子視窗。|
|[CMDIFramewnd::獲取視窗功能表彈出](#getwindowmenupopup)|返回"視窗"彈出式功能表。|
|[CMDIFramewnd::MDIActivate](#mdiactivate)|啟動其他 MDI 子視窗。|
|[CMDIFramewnd::MDICascade](#mdicascade)|以級聯格式排列所有子視窗。|
|[CMDIFramewnd:MDIGetactive](#mdigetactive)|檢索當前活動的 MDI 子視窗,以及指示子項是否最大化的標誌。|
|[CMDIFramewnd::MDIIcon排列](#mdiiconarrange)|排列所有最小化的文檔子視窗。|
|[CMDIFramewnd::MDI最大化](#mdimaximize)|最大化 MDI 子視窗。|
|[CMDIFramewnd::MDINext](#mdinext)|立即啟動當前活動子視窗後面的子視窗,並將當前處於活動狀態的子視窗放在所有其他子窗口後面。|
|[CMDIFramewnd::MDIPrev](#mdiprev)|啟動以前的子視窗,並將當前處於活動狀態的子視窗立即放在視窗後面。|
|[CMDIFramewnd::MDI還原](#mdirestore)|從最大大小或最小化大小還原 MDI 子視窗。|
|[CMDIFramewnd::MDISetMenu](#mdisetmenu)|替換 MDI 框架視窗的功能表、視窗彈出視窗功能表或兩者。|
|[CMDIFramewnd::MDITile](#mditile)|以平鋪格式排列所有子視窗。|

## <a name="remarks"></a>備註

要為應用程式創建有用的 MDI 框架視窗,`CMDIFrameWnd`請從 派生類。 將成員變數添加到派生類以存儲特定於應用程式的數據。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。

可以通過呼叫 的[「建立](../../mfc/reference/cframewnd-class.md#create)」 或[「LoadFrame」](../../mfc/reference/cframewnd-class.md#loadframe)成員函數`CFrameWnd`來建構 MDI 畫面視窗 。

在調用`Create``LoadFrame`或之前,必須**使用新運算符**C++在堆上構造幀視窗物件。 在調用`Create`之前,您還可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函數註冊視窗類,以設置框架的圖示和類樣式。

使用`Create`成員函數將幀的創建參數作為即時參數傳遞。

`LoadFrame`需要的參數少於`Create`,而是從資源檢索其大部分預設值,包括框架的標題、圖示、快速鍵表和菜單。 要由`LoadFrame`訪問,所有這些資源必須具有相同的資源 ID(例如,IDR_MAINFRAME)。

儘管`MDIFrameWnd`派生`CFrameWnd`自 ,但`CMDIFrameWnd``DECLARE_DYNCREATE`不需要使用 聲明派生的幀視窗類。

類`CMDIFrameWnd``CFrameWnd`從 繼承其大部分預設實現。 有關這些功能的詳細清單,請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類說明。 該`CMDIFrameWnd`類別有以下附加功能:

- MDI 框架視窗管理 MDICLIENT 視窗,將其與控制列一起重新置放。 MDI 用戶端視窗是 MDI 子框架視窗的直接父級。 在 DDI 用戶端視窗`CMDIFrameWnd`而不是主 框架視窗上指定的WS_HSCROLL和WS_VSCROLL視窗樣式,以便使用者可以滾動 MDI 工作區(例如,如 Windows 程式管理器中所示)。

- MDI 框架視窗具有預設功能表,當沒有活動 MDI 子視窗時,該功能表用作選單欄。 當存在活動 MDI 子項時,MDI 框架視窗的功能表列將自動取代為 MDI 子視窗功能表。

- MDI 框架視窗與目前的 MDI 子視窗(如果有)配合使用。 例如,命令消息在 MDI 幀視窗之前委派給當前活動的 MDI 子級。

- MDI 框架視窗具有以下標準視窗選單指令的預設處理程式:

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- MDI 框架視窗還具有ID_WINDOW_NEW的實現,從而在當前文檔上創建新的幀和視圖。 應用程式可以重寫這些預設命令實現以自定義 MDI 視窗處理。

請勿使用C++**刪除**運算元來破壞框架視窗。 請改用 `CWnd::DestroyWindow`。 當`CFrameWnd`視窗`PostNcDestroy`被破壞時,將刪除C++物件。 當使用者關閉畫面視窗時,預設`OnClose`處理程式將呼`DestroyWindow`叫 。

有關 的詳細`CMDIFrameWnd`資訊 ,請參閱[框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFramewnd::CMDIFramewnd

建構 `CMDIFrameWnd` 物件。

```
CMDIFrameWnd();
```

### <a name="remarks"></a>備註

呼叫`Create``LoadFrame`或 成員函數以建立可見的 MDI 幀視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFramewnd::創建用戶端

建立管理`CMDIChildWnd`物件的 MDI 用戶端視窗。

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>參數

*lpCreatestruct*<br/>
指向[CREATESTRUCT 結構](/windows/win32/api/winuser/ns-winuser-createstructw)的長指標。

*pWindowMenu*<br/>
指向視窗彈出功能表的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果直接重寫成員函數,`OnCreate`則應呼叫此成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFramewnd::創建新兒童

創建新的子視窗。

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>參數

*pClass*<br/>
要創建的子視窗的運行時類。

*n資源*<br/>
與子視窗關聯的共享資源的 ID。

*hMenu*<br/>
子視窗的功能表。

*哈克爾*<br/>
子視窗的加速器。

### <a name="remarks"></a>備註

使用此函數可以創建 MDI 框架視窗的子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFramewnd::獲取視窗功能表彈出

呼叫此成員函數以取得目前的名為「視窗」的彈出式選單(包含 MDI 視窗管理的功能表項目的彈出功能表)的句柄。

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>參數

*hMenuBar*<br/>
當前功能表欄。

### <a name="return-value"></a>傳回值

視窗彈出功能表(如果存在);否則 NULL。

### <a name="remarks"></a>備註

默認實現查找包含標準視窗功能表命令(如ID_WINDOW_NEW和ID_WINDOW_TILE_HORZ)的彈出功能表。

如果視窗功能表不使用標準選單命令"指示",則覆蓋此成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFramewnd::MDIActivate

啟動其他 MDI 子視窗。

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>參數

*pWndActivate*<br/>
指向要啟動的 MDI 子視窗。

### <a name="remarks"></a>備註

此成員函數向正在啟動的子視窗和正在停用的子視窗發送[WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate)訊息。

如果使用者使用滑鼠或鍵盤將焦點更改為 MDI 子視窗,則發送的消息與發送的消息相同。

> [!NOTE]
> 獨立於 MDI 框架視窗啟動 MDI 子視窗。 當幀變為活動狀態時,上次啟動的子視窗將發送[一條WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate)消息以繪製活動視窗框和標題列,但不會收到另一WM_MDIACTIVATE消息。

### <a name="example"></a>範例

請參考[CMDIFrameWnd 的範例:抓取視窗選單彈出](#getwindowmenupopup)。

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFramewnd::MDICascade

以級聯格式排列所有 MDI 子視窗。

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>參數

*nType*<br/>
指定級聯標誌。 只能指定以下標誌:MDITILE_SKIPDISABLED,以防止禁用的 MDI 子視窗被級聯。

### <a name="remarks"></a>備註

第一個版本`MDICascade`沒有參數,級聯所有 MDI 子視窗,包括禁用的。 如果為*nType*參數指定MDITILE_SKIPDISABLED,則第二個版本可選地不會級聯禁用的 MDI 子視窗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFramewnd:MDIGetactive

檢索當前活動 MDI 子視窗,以及指示子視窗是否最大化的標誌。

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>參數

*pb 最大化*<br/>
指向 BOOL 返回值的指標。 如果視窗最大化,則在返回時設置為 TRUE;如果視窗最大化,則設置為 TRUE。否則 FALSE。

### <a name="return-value"></a>傳回值

指向活動 MDI 子視窗的指標。

### <a name="example"></a>範例

請參閱[CMDIChildwnd 的範例::MDI最大化](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFramewnd::MDIIcon排列

排列所有最小化的文檔子視窗。

```
void MDIIconArrange();
```

### <a name="remarks"></a>備註

它不會影響未最小化的子視窗。

### <a name="example"></a>範例

請參閱[CMDIFrameWnd 的範例::MDICascade](#mdicascade)。

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFramewnd::MDI最大化

最大化指定的 MDI 子視窗。

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向視窗以最大化。

### <a name="remarks"></a>備註

最大化子視窗時,Windows會調整其大小,使其工作區填充用戶端視窗。 Windows 將子視窗的「控制件」功能表放在框架的功能表欄中,以便用戶可以還原或關閉子視窗。 它還將子視窗的標題添加到框架視窗標題。

如果在最大化當前活動的 MDI 子視窗時啟動另一個 MDI 子視窗,Windows 將恢復目前處於活動狀態的子視窗並最大化新啟動的子視窗。

### <a name="example"></a>範例

請參閱[CMDIChildwnd 的範例::MDI最大化](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFramewnd::MDINext

立即啟動當前活動子視窗後面的子視窗,並將當前處於活動狀態的子視窗放在所有其他子窗口後面。

```
void MDINext();
```

### <a name="remarks"></a>備註

如果當前活動的 MDI 子視窗最大化,則成員函數將恢復當前處於活動狀態的子級並最大化新啟動的子級。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFramewnd::MDIPrev

啟動以前的子視窗,並將當前處於活動狀態的子視窗立即放在視窗後面。

```
void MDIPrev();
```

### <a name="remarks"></a>備註

如果當前活動的 MDI 子視窗最大化,則成員函數將恢復當前處於活動狀態的子級並最大化新啟動的子級。

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFramewnd::MDI還原

從最大大小或最小化大小還原 MDI 子視窗。

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向要還原的視窗。

### <a name="example"></a>範例

請參閱[CMDIChildwnd 的範例::MDI 還原](../../mfc/reference/cmdichildwnd-class.md#mdirestore)。

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFramewnd::MDISetMenu

替換 MDI 框架視窗的功能表、視窗彈出視窗功能表或兩者。

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>參數

*pFrameMenu*<br/>
指定新框架視窗功能表的選單。 如果為 NULL,則功能表不會更改。

*pWindowMenu*<br/>
指定新視窗彈出式功能表的功能表。 如果為 NULL,則功能表不會更改。

### <a name="return-value"></a>傳回值

指向由此消息替換的框架視窗功能表的指標。 該指標可能是暫時性的，因此不應該儲存供日後使用。

### <a name="remarks"></a>備註

呼叫`MDISetMenu`後,應用程式必須調用`CWnd`的[DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成員函數來更新功能表欄。

如果此調用替換視窗彈出視窗功能表,則 MDI 子視窗功能表項將從上一個視窗選單中刪除,並添加到新的視窗彈出視窗功能表中。

如果最大化 MDI 子視窗,並且此調用替換 MDI 框架視窗功能表,則「控制」功能表和還原控制項將從以前的框架視窗功能表中刪除並添加到新功能表。

如果使用框架管理 MDI 子視窗,請不要呼叫此成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFramewnd::MDITile

以平鋪格式排列所有子視窗。

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>參數

*nType*<br/>
指定平鋪標誌。 這裡可以是以下旗標之一:

- MDITILE_HORIZONTAL磁貼 MDI 子視窗,以便一個視窗顯示在另一個視窗的上方。

- MDITILE_SKIPDISABLED防止禁用的 MDI 子視窗被平鋪。

- MDITILE_VERTICAL磁貼 MDI 子視窗,以便一個視窗出現在另一個視窗旁邊。

### <a name="remarks"></a>備註

第一個版本`MDITile`沒有參數,在 Windows 版本 3.1 和更高版本下垂直放置視窗。 第二個版本垂直或水準地放置視窗,具體取決於*nType*參數的值。

### <a name="example"></a>範例

請參閱[CMDIFrameWnd 的範例::MDICascade](#mdicascade)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)
