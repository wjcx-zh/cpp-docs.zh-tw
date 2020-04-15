---
title: 訊息對應巨集 (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356590"
---
# <a name="message-map-macros-mfc"></a>訊息對應巨集 (MFC)

若要支援訊息對應，MFC 提供下列巨集：

### <a name="message-map-declaration-and-demarcation-macros"></a>訊息對應宣告和分界巨集

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|宣告的訊息對應會使用類別將訊息與函式對應 (必須在類別宣告中使用)。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|開始進行訊息對應的定義 (必須在類別實作中使用)。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|開始在包含單個範本參數的類類型上定義消息對應。 |
|[END_MESSAGE_MAP](#end_message_map)|結束訊息對應的定義 (必須在類別實作中使用)。|

### <a name="message-mapping-macros"></a>訊息對應巨集

|||
|-|-|
|[ON_COMMAND](#on_command)|指出哪些函式會處理指定的命令訊息。|
|[ON_COMMAND_EX](#on_command_ex)|指出哪些函式會處理指定的命令訊息。|
|[ON_CONTROL](#on_control)|指出哪些函式會處理指定的控制項通知訊息。|
|[ON_MESSAGE](#on_message)|指出哪些函式會處理使用者定義的訊息。|
|[ON_OLECMD](#on_olecmd)|指出哪些函式會處理來自 DocObject 或其容器的功能表命令。|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|指出哪些函式會處理已註冊的使用者定義訊息。|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|指出當您擁有 `CWinThread` 類別時，哪些函式會處理已註冊的使用者定義訊息。|
|[ON_THREAD_MESSAGE](#on_thread_message)|指出當您擁有 `CWinThread` 類別時，哪些函式會處理使用者定義的訊息。|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|指出哪些函式會處理指定的使用者介面更新命令訊息。|

### <a name="message-map-range-macros"></a>訊息對應範圍巨集

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|指出哪些函式會處理巨集的前兩個參數中指定之命令 ID 的範圍。|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|指出哪些更新處理常式會處理在巨集前兩個參數中指定之命令 ID 的範圍。|
|[ON_CONTROL_RANGE](#on_control_range)|指出哪些函式會處理來自在巨集的第二和第三個參數中指定之控制項 ID 範圍的通知。 第一個參數是一個控制項通知訊息，例如 BN_CLICKED。|

有關訊息映射、訊息映射聲明和標界宏以及消息對應巨集的詳細資訊,請參閱[訊息映射](../../mfc/reference/message-maps-mfc.md)和[訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。 有關訊息映射範圍的詳細資訊,請參閱[訊息映射範圍的處理程式](../../mfc/handlers-for-message-map-ranges.md)。

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

開始定義消息映射。

### <a name="syntax"></a>語法

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*類別*<br/>
指定消息映射為該類的類的名稱。

*基類*<br/>
指定*類*的基類的名稱。

### <a name="remarks"></a>備註

在定義類成員函數的實現 (.cpp) 檔中,使用BEGIN_MESSAGE_MAP宏啟動消息映射,然後為每個消息處理程式函數添加宏條目,然後使用END_MESSAGE_MAP宏完成消息映射。

有關消息映射的詳細資訊,請參閱[消息映射](message-maps-mfc.md)

### <a name="example"></a>範例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

開始在包含單個範本參數的類類型上定義消息對應。

### <a name="syntax"></a>語法

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>參數

*類別*<br/>
指定消息映射為該類的類的名稱。

*type_name*<br/>
為類指定的範本參數的名稱。

*基類*<br/>
指定*類*的基類的名稱。

### <a name="remarks"></a>備註

此宏類似於[BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map)宏;但是,此宏適用於包含單個範本參數的類。

在類的方法實現部分中,使用BEGIN_TEMPLATE_MESSAGE_MAP宏啟動消息映射;在類中,使用 BEGIN_TEMPLATE_MESSAGE_MAP 宏啟動消息映射。然後,像為標準消息映射添加每個消息處理程式方法的宏條目。 與BEGIN_MESSAGE_MAP宏一樣,使用[END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map)宏完成範本消息映射。

有關實現範本類的消息對應的詳細資訊,請參閱[如何:為樣本類別建立消息映射](../how-to-create-a-message-map-for-a-template-class.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

聲明類定義消息映射。 程式中`CCmdTarget`的每個派生類必須提供消息映射來處理消息。

### <a name="syntax"></a>語法

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>備註

在類聲明末尾使用DECLARE_MESSAGE_MAP宏。 然後,在定義類成員函數的 .cpp 檔中,使用BEGIN_MESSAGE_MAP宏、每個消息處理程式函數的宏條目和END_MESSAGE_MAP宏。

> [!NOTE]
> 如果在DECLARE_MESSAGE_MAP後聲明任何成員,則必須為其指定新的訪問類型(**公共**、**私有**或**受保護**)。

有關消息對應和DECLARE_MESSAGE_MAP宏的詳細資訊,請參閱[訊息處理和映射主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

結束訊息對應的定義。

### <a name="syntax"></a>語法

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>備註

有關消息對應和END_MESSAGE_MAP宏的詳細資訊,請參閱[訊息處理和映射主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

此宏將命令消息映射到成員函數。

### <a name="syntax"></a>語法

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>參數

*命令代碼*<br/>
命令 ID。

*成員Fxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

它指示哪個函數將處理來自命令使用者介面物件(如功能表項或工具列按鈕)的命令訊息。

當命令目標物件收到帶有指定 ID 的 Windows WM_COMMAND 消息時,ON_COMMAND將調用成員`memberFxn`函數來處理該消息。

使用ON_COMMAND將單個命令映射到成員函數。 使用[ON_COMMAND_RANGE](#on_command_range)將命令指示數範圍映射到一個成員函數。 只有一個消息映射條目可以匹配給定的命令 ID。 也就是說,不能將命令映射到多個處理程式。 有關詳細資訊和範例,請參閱[訊息處理與映射主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

擴展的命令處理程式成員函數。

### <a name="syntax"></a>語法

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>參數

*命令代碼*<br/>
命令 ID。

*成員Fxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

命令消息處理程式的擴展形式可用於高級用途。 ON_COMMAND_EX宏用於此類消息處理程式,它提供了[ON_COMMAND](message-map-macros-mfc.md#on_command)功能的超集。 擴展的命令處理程式成員函數採用單個參數,一個包含命令 ID 的 UINT,並返回 BOOL。 返回值應為 TRUE,以指示已處理命令;因此,返回值應為 TRUE,以指示該命令已處理。否則路由將繼續到其他命令目標物件。

有關詳細資訊,請參閱技術說明 [TN006:消息映射]tm006 消息-maps.md)。

### <a name="requirements"></a>需求

標頭檔: afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

指示哪個函數將處理自定義控制通知消息。

### <a name="syntax"></a>語法

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>參數

*wNotifyCode*<br/>
控制項的通知代碼。

*命令代碼*<br/>
命令 ID。

*成員Fxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

控件通知消息是從控制件發送到其父視窗的消息。

對於必須映射到消息處理程式函數的每個控制項通知消息,消息映射中應有一個ON_CONTROL宏語句。

有關詳細資訊和範例,請參閱[訊息處理與映射主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

指出哪些函式會處理使用者定義的訊息。

### <a name="syntax"></a>語法

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>參數

*訊息*<br/>
訊息 ID。

*成員Fxn*<br/>
消息映射到的消息處理程式函數的名稱。

函數的類型必須為`afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`。

### <a name="remarks"></a>備註

使用者定義的消息不是標準 Windows WM_MESSAGE消息的任何消息。 選擇消息 ID 時,必須使用 WM_USER (0x0400) 到 0x7FFF 或 WM_APP (0x8000) 到 0xBFFF 範圍內的值。 有關訊息指示的詳細資訊,請參閱[WM_APP](/windows/win32/winmsg/wm-app)。

對於必須映射到消息處理程式函數的每個使用者定義的消息,消息映射中應有一個ON_MESSAGE宏語句。

> [!NOTE]
> 除了用戶定義的消息外,ON_MESSAGE處理不太常見的 Windows 消息。 有關詳細資訊,請參閱[訊息映射](../../mfc/tn006-message-maps.md)。

有關詳細資訊和範例,請參閱[訊息處理和映射主題](../../mfc/message-handling-and-mapping.md)和[使用者定義的處理程式](user-defined-handlers.md)

### <a name="example"></a>範例

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

通過命令調度介面`IOleCommandTarget`路由命令。

### <a name="syntax"></a>語法

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>參數

*普吉德*<br/>
指令所屬的命令組的識別碼。 對標準群組使用 NULL。

*奧萊姆迪*<br/>
OLE 命令的標識碼。

*命令代碼*<br/>
發出命令的資源或物件的功能表 ID、工具列 ID、按鈕 ID 或其他 ID。

### <a name="remarks"></a>備註

`IOleCommandTarget`允許容器接收源自 DocObject 使用者介面的命令,並允許容器向 DocObject 發送相同的命令(如"新建"、"打開"、"保存"和"在檔"功能表上列印;在"編輯"功能表上複製、粘貼、撤消等)。

`IOleCommandTarget`比 OLE 自動化`IDispatch`更簡單 。 `IOleCommandTarget`完全依賴於一組很少有參數的標準命令,並且不涉及類型資訊(命令參數的類型安全性也降低)。 如果確實需要使用參數調度指令,請使用[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)。

`IOleCommandTarget`標準選單指令已由 MFC 在以下宏中實現:

**ON_OLECMD_CLEARSELECTION)**

調度編輯清除命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY)**

調度編輯複製命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT)**

調度"編輯剪切"命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW)**

調度檔新命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN)**

調度文件打開命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP)**

調度檔頁設置命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE)**

調度編輯粘貼命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL)**

調度編輯粘貼特殊命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT)**

調度檔列印命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW)**

調度檔列印預覽命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO)**

調度編輯重做命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE)**

調度檔保存命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS)**

調度檔保存為命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS)**

調度檔保存副本作為命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL)**

調度"編輯選擇全部"命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO)**

調度編輯復原命令。 實施方式如下:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>需求

**標題:** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Windows`RegisterWindowMessage`函數用於定義保證在整個系統中唯一的新視窗消息。

### <a name="syntax"></a>語法

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>參數

*nMessageVariable*<br/>
已註冊的視窗消息 ID 變數。

*成員Fxn*<br/>
消息映射到的消息處理程式函數的名稱。

### <a name="remarks"></a>備註

此宏指示哪個函數將處理已註冊的消息。

有關詳細資訊和範例,請參閱[訊息處理與映射主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

指示哪個函數將處理 Windows 註冊視窗消息功能註冊的消息。

### <a name="syntax"></a>語法

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>參數

*nMessageVariable*<br/>
已註冊的視窗消息 ID 變數。

*成員Fxn*<br/>
消息映射到的 CWinThread 消息處理程式函數的名稱。

### <a name="remarks"></a>備註

註冊視窗消息用於定義保證在整個系統中唯一的新視窗消息。 當您有 CWinThread 類時,必須使用 ON_REGISTERED_THREAD_MESSAGE而不是ON_REGISTERED_MESSAGE。

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

指出哪些函式會處理使用者定義的訊息。

### <a name="syntax"></a>語法

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>參數

*訊息*<br/>
訊息 ID。

*成員Fxn*<br/>
消息映射到的`CWinThread`-消息處理程式函數的名稱。

### <a name="remarks"></a>備註

當您有`CWinThread`類時,必須使用ON_THREAD_MESSAGE而不是ON_MESSAGE。 使用者定義的消息不是標準 Windows WM_MESSAGE消息的任何消息。 對於必須映射到消息處理程式函數的每個使用者定義的消息,消息映射中應有一個ON_THREAD_MESSAGE宏語句。

### <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

此宏指示哪個函數將處理使用者介面更新命令消息。

### <a name="syntax"></a>語法

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>參數

*訊息代碼*<br/>
訊息 ID。

*成員Fxn*<br/>
消息映射到的消息處理程式函數的名稱。

### <a name="remarks"></a>備註

對於必須映射到消息處理程式函數的每個使用者介面更新命令,消息映射中應有一個ON_UPDATE_COMMAND_UI宏語句。

有關詳細資訊和範例,請參閱[訊息處理與映射主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

使用此宏將連續範圍的命令指示數映射到單個消息處理程式函數。

### <a name="syntax"></a>語法

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*id1*<br/>
連續命令 ID 範圍開頭的命令 ID。

*id2*<br/>
連續命令 ID 範圍末尾的命令 ID。

*成員Fxn*<br/>
命令映射到的消息處理程式函數的名稱。

### <a name="remarks"></a>備註

ID 的範圍從*id1*開始,以*id2*結尾。

使用ON_COMMAND_RANGE將命令指示數範圍映射到一個成員函數。 使用[ON_COMMAND](#on_command)將單個命令映射到成員函數。 只有一個消息映射條目可以匹配給定的命令 ID。 也就是說,不能將命令映射到多個處理程式。 有關映射訊息範圍的詳細資訊,請參閱[訊息映射範圍的處理程式](../../mfc/handlers-for-message-map-ranges.md)。

沒有自動支援消息映射範圍,因此您必須自己放置宏。

### <a name="example"></a>範例

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

將連續範圍的命令指示映射到單個更新消息處理程式函數。

### <a name="syntax"></a>語法

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*id1*<br/>
連續命令 ID 範圍開頭的命令 ID。

*id2*<br/>
連續命令 ID 範圍末尾的命令 ID。

*成員Fxn*<br/>
命令對應到的更新訊息處理程式函數的名稱。

### <a name="remarks"></a>備註

更新消息處理程式更新與命令關聯的功能表項和工具列按鈕的狀態。 ID 的範圍從*id1*開始,以*id2*結尾。

沒有自動支援消息映射範圍,因此您必須自己放置宏。

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

使用此宏可將連續控制項 I 範圍映射到指定 Windows 通知訊息的單個訊息處理程式函數,如BN_CLICKED。

### <a name="syntax"></a>語法

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*wNotifyCode*<br/>
處理程式正在回應的通知代碼。

*id1*<br/>
連續控制 ID 範圍開頭的命令 ID。

*id2*<br/>
連續控制 ID 範圍末尾的命令 ID。

*成員Fxn*<br/>
將控制項映射到的消息處理程式函數的名稱。

### <a name="remarks"></a>備註

ID 的範圍從*id1*開始,以*id2*結尾。 對於來自任何映射的控制項的指定通知,調用處理程式。

沒有自動支援消息映射範圍,因此您必須自己放置宏。

有關實現一系列控制軟體 I 的處理程式函數的詳細資訊,請參閱[訊息映射範圍的處理程式](../../mfc/handlers-for-message-map-ranges.md)。

### <a name="requirements"></a>需求

**標題:** afxmsg_.h

## <a name="see-also"></a>另請參閱

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006：訊息對應](../tn006-message-maps.md)<br/>
[COleCmdUI 類別](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[註冊視窗訊息](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[使用者定義的處理常式](user-defined-handlers.md)<br/>
[CCmdUI 類別](ccmdui-class.md)
