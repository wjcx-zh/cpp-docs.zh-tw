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
ms.openlocfilehash: 33b5d2eaefa11f9ccf6459aa05b4e24138731e80
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840267"
---
# <a name="message-map-macros-mfc"></a>訊息對應巨集 (MFC)

若要支援訊息對應，MFC 提供下列巨集：

### <a name="message-map-declaration-and-demarcation-macros"></a>訊息對應宣告和分界巨集

|名稱|描述|
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|宣告的訊息對應會使用類別將訊息與函式對應 (必須在類別宣告中使用)。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|開始進行訊息對應的定義 (必須在類別實作中使用)。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|開始在包含單一樣板引數的類別型別上進行訊息對應的定義。 |
|[END_MESSAGE_MAP](#end_message_map)|結束訊息對應的定義 (必須在類別實作中使用)。|

### <a name="message-mapping-macros"></a>訊息對應巨集

|名稱|描述|
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

|名稱|描述|
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|指出哪些函式會處理巨集的前兩個參數中指定之命令 ID 的範圍。|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|指出哪些更新處理常式會處理在巨集前兩個參數中指定之命令 ID 的範圍。|
|[ON_CONTROL_RANGE](#on_control_range)|指出哪些函式會處理來自在巨集的第二和第三個參數中指定之控制項 ID 範圍的通知。 第一個參數是一個控制項通知訊息，例如 BN_CLICKED。|

如需訊息對應、訊息對應宣告和分界宏以及訊息對應宏的詳細資訊，請參閱 [訊息對應](../../mfc/reference/message-maps-mfc.md) 和 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。 如需訊息對應範圍的詳細資訊，請參閱 [訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。

## <a name="begin_message_map"></a><a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

開始訊息對應的定義。

### <a name="syntax"></a>語法

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定訊息對應所屬類別的名稱。

*baseClass*<br/>
指定 *theClass*基類的名稱。

### <a name="remarks"></a>備註

在為您的類別定義成員函式的 ( .cpp) 檔中，使用 BEGIN_MESSAGE_MAP 宏啟動訊息對應，然後為每個訊息處理常式函式加入宏專案，然後使用 END_MESSAGE_MAP 宏完成訊息對應。

如需訊息對應的詳細資訊，請參閱 [訊息對應](message-maps-mfc.md)

### <a name="example"></a>範例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a> BEGIN_TEMPLATE_MESSAGE_MAP

開始在包含單一樣板引數的類別型別上進行訊息對應的定義。

### <a name="syntax"></a>語法

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定訊息對應所屬類別的名稱。

*type_name*<br/>
為類別指定之範本參數的名稱。

*baseClass*<br/>
指定 *theClass*基類的名稱。

### <a name="remarks"></a>備註

這個宏類似于 [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) 宏;不過，此宏適用于包含單一範本引數的類別。

在類別的方法執行區段中，以 BEGIN_TEMPLATE_MESSAGE_MAP 宏啟動訊息對應;然後，為每個訊息處理常式方法加入宏專案，就像您針對標準訊息對應所做的一樣。 如同 BEGIN_MESSAGE_MAP 宏一樣，使用 [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) 宏完成範本訊息對應。

如需有關如何針對範本類別來執行訊息對應的詳細資訊，請參閱 [如何：建立樣板類別的訊息對應](../how-to-create-a-message-map-for-a-template-class.md)。

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a> DECLARE_MESSAGE_MAP

宣告類別會定義訊息對應。 `CCmdTarget`程式中的每個衍生類別都必須提供訊息對應來處理訊息。

### <a name="syntax"></a>語法

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>備註

在類別宣告的結尾使用 DECLARE_MESSAGE_MAP 宏。 然後，在定義類別成員函式的 .cpp 檔案中，使用 BEGIN_MESSAGE_MAP 宏、每個訊息處理常式函式的宏專案，以及 END_MESSAGE_MAP 宏。

> [!NOTE]
> 如果您在 DECLARE_MESSAGE_MAP 之後宣告任何成員，您必須為這些成員指定新的存取類型 (**`public`** 、 **`private`** 或 **`protected`**) 。

如需訊息對應和 DECLARE_MESSAGE_MAP 宏的詳細資訊，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a> END_MESSAGE_MAP

結束訊息對應的定義。

### <a name="syntax"></a>語法

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>備註

如需訊息對應和 END_MESSAGE_MAP 宏的詳細資訊，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a> ON_COMMAND

此宏會將命令訊息對應到成員函式。

### <a name="syntax"></a>語法

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>參數

*commandId*<br/>
命令 ID。

*memberFxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

它會指出哪一個函式會從命令使用者介面物件（例如功能表項目或工具列按鈕）處理命令訊息。

當命令目標物件收到具有指定識別碼的 Windows WM_COMMAND 訊息時，ON_COMMAND 會呼叫成員函式 `memberFxn` 來處理訊息。

使用 ON_COMMAND 將單一命令對應到成員函式。 使用 [ON_COMMAND_RANGE](#on_command_range) 將某個範圍的命令識別碼對應至一個成員函式。 只有一個訊息對應專案可以符合指定的命令識別碼。 也就是說，您無法將命令對應到一個以上的處理常式。 如需詳細資訊和範例，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_command_ex"></a><a name="on_command_ex"></a> ON_COMMAND_EX

擴充的命令處理常式成員函式。

### <a name="syntax"></a>語法

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>參數

*commandId*<br/>
命令 ID。

*memberFxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

有擴充形式的命令訊息處理常式可供 advanced 使用。 ON_COMMAND_EX 宏用於這類訊息處理常式，並提供 [ON_COMMAND](message-map-macros-mfc.md#on_command) 功能的超集合。 擴充的命令處理常式成員函式會採用單一參數、包含命令識別碼的 UINT，並傳回 BOOL。 傳回值應為 TRUE，表示已處理命令;否則路由將繼續前往其他命令目標物件。

如需詳細資訊，請參閱技術附注 [TN006： Message Map] tm006-Message maps.md) 。

### <a name="requirements"></a>規格需求

標頭檔： afxmsg_。h

## <a name="on_control"></a><a name="on_control"></a> ON_CONTROL

指出哪些函式會處理自訂控制項通知訊息。

### <a name="syntax"></a>語法

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>參數

*wNotifyCode*<br/>
控制項的通知碼。

*commandId*<br/>
命令 ID。

*memberFxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

控制項通知訊息是從控制項傳送至其父視窗的通知訊息。

在訊息對應中，每個必須對應至訊息處理常式函式的控制項通知訊息，都應該剛好有一個 ON_CONTROL 巨集式。

如需詳細資訊和範例，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_message"></a><a name="on_message"></a> ON_MESSAGE

指出哪些函式會處理使用者定義的訊息。

### <a name="syntax"></a>語法

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>參數

*message*<br/>
訊息 ID。

*memberFxn*<br/>
訊息所對應的訊息處理函式名稱。

函數的型別必須是 `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)` 。

### <a name="remarks"></a>備註

使用者定義的訊息是指不是標準 Windows WM_MESSAGE 訊息的任何訊息。 選取訊息識別碼時，您必須使用 WM_USER (0x0400) 範圍內的值來0x7FFF 或 WM_APP (0x8000) 到0xBFFF。 如需有關訊息識別碼的詳細資訊，請參閱 [WM_APP](/windows/win32/winmsg/wm-app)。

在您的訊息對應中，每個必須對應至訊息處理函式的使用者自訂訊息，都應該剛好有一個 ON_MESSAGE 巨集式。

> [!NOTE]
> 除了使用者定義的訊息之外，ON_MESSAGE 也會處理較少的常見 Windows 訊息。 如需詳細資訊，請參閱 [訊息對應](../../mfc/tn006-message-maps.md)。

如需詳細資訊和範例，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md) 以及 [使用者定義的處理常式](user-defined-handlers.md)

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

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_olecmd"></a><a name="on_olecmd"></a> ON_OLECMD

透過命令分派介面路由命令 `IOleCommandTarget` 。

### <a name="syntax"></a>語法

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>參數

*pguid*<br/>
命令所屬命令組的識別碼。 針對標準群組，請使用 Null。

*olecmdid*<br/>
OLE 命令的識別碼。

*commandId*<br/>
發出命令之資源或物件的功能表識別碼、工具列識別碼、按鈕識別碼或其他識別碼。

### <a name="remarks"></a>備註

`IOleCommandTarget` 允許容器接收源自于 DocObject 之使用者介面的命令，並允許容器傳送相同的命令 (例如 [檔案] 功能表上的 [新增]、[開啟]、[另存新檔] 和 [列印];然後將 [編輯] 功能表上的 [複製]、[貼上]、[復原] 和 [複製]) DocObject。

`IOleCommandTarget` 比 OLE Automation 簡單得多 `IDispatch` 。 `IOleCommandTarget` 完全依賴一組不常有引數的標準命令，而不會涉及任何類型資訊 (型別安全對於命令引數的) 也會降低。 如果您需要分派具有引數的命令，請使用 [COleServerDoc：： OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)。

`IOleCommandTarget`標準功能表命令已由 MFC 在下列宏中執行：

**ON_OLECMD_CLEARSELECTION ( ) **

分派 Edit Clear 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY ( ) **

分派編輯複製命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT ( ) **

分派 [編輯剪下] 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW ( ) **

分派 File New 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN ( ) **

分派 File Open 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP ( ) **

分派檔案頁面安裝命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE ( ) **

分派編輯貼上命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL ( ) **

分派編輯貼上特殊命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT ( ) **

分派檔案列印命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW ( ) **

分派檔案預覽列印命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO ( ) **

分派編輯重做命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE ( ) **

分派 File Save 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS ( ) **

分派 File Save As 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS ( ) **

分派 File Save Copy As 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL ( ) **

分派 [編輯全選] 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO ( ) **

分派 [編輯復原] 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>規格需求

**標頭：** afxdocob。h

## <a name="on_registered_message"></a><a name="on_registered_message"></a> ON_REGISTERED_MESSAGE

Windows `RegisterWindowMessage` 函數用來定義新的視窗訊息，在整個系統中保證是唯一的。

### <a name="syntax"></a>語法

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>參數

*nMessageVariable*<br/>
已註冊的視窗訊息識別碼變數。

*memberFxn*<br/>
訊息所對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

此宏指出哪些函式會處理已註冊的訊息。

如需詳細資訊和範例，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a> ON_REGISTERED_THREAD_MESSAGE

指出哪些函式會處理 Windows RegisterWindowMessage 函數所註冊的訊息。

### <a name="syntax"></a>語法

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>參數

*nMessageVariable*<br/>
已註冊的視窗訊息識別碼變數。

*memberFxn*<br/>
訊息所對應之 CWinThread 訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

RegisterWindowMessage 是用來定義新的視窗訊息，在整個系統中保證是唯一的。 當您有 CWinThread 類別時，必須使用 ON_REGISTERED_THREAD_MESSAGE 而不是 ON_REGISTERED_MESSAGE。

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_thread_message"></a><a name="on_thread_message"></a> ON_THREAD_MESSAGE

指出哪些函式會處理使用者定義的訊息。

### <a name="syntax"></a>語法

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>參數

*message*<br/>
訊息 ID。

*memberFxn*<br/>
訊息所對應的 `CWinThread` 訊息處理函式名稱。

### <a name="remarks"></a>備註

當您有類別時，必須使用 ON_THREAD_MESSAGE 而不是 ON_MESSAGE `CWinThread` 。 使用者定義的訊息是指不是標準 Windows WM_MESSAGE 訊息的任何訊息。 在您的訊息對應中，每個必須對應至訊息處理函式的使用者自訂訊息，都應該剛好有一個 ON_THREAD_MESSAGE 巨集式。

### <a name="requirements"></a>規格需求

**標頭：** afxole。h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a> ON_UPDATE_COMMAND_UI

此宏會指出哪一個函式將會處理使用者介面更新命令訊息。

### <a name="syntax"></a>語法

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>參數

*messageId*<br/>
訊息 ID。

*memberFxn*<br/>
訊息所對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

在您的訊息對應中，每個必須對應至訊息處理函式的使用者介面更新命令都應該剛好有一個 ON_UPDATE_COMMAND_UI 巨集式。

如需詳細資訊和範例，請參閱 [訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxole。h

## <a name="on_command_range"></a><a name="on_command_range"></a> ON_COMMAND_RANGE

使用這個宏可將連續範圍的命令識別碼對應至單一訊息處理常式函式。

### <a name="syntax"></a>語法

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*id1*<br/>
命令識別碼的連續範圍開頭的命令識別碼。

*id2*<br/>
命令識別碼連續範圍結尾的命令識別碼。

*memberFxn*<br/>
命令所對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

識別碼的範圍會以 *id1* 開頭，並以 *id2*結尾。

使用 ON_COMMAND_RANGE 將某個範圍的命令識別碼對應至一個成員函式。 使用 [ON_COMMAND](#on_command) 將單一命令對應到成員函式。 只有一個訊息對應專案可以符合指定的命令識別碼。 也就是說，您無法將命令對應到一個以上的處理常式。 如需對應訊息範圍的詳細資訊，請參閱 [訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。

訊息對應範圍沒有自動支援，因此您必須自行放置宏。

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

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a> ON_UPDATE_COMMAND_UI_RANGE

將連續的命令識別碼範圍對應至單一更新訊息處理常式函數。

### <a name="syntax"></a>語法

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*id1*<br/>
命令識別碼的連續範圍開頭的命令識別碼。

*id2*<br/>
命令識別碼連續範圍結尾的命令識別碼。

*memberFxn*<br/>
命令所對應的更新訊息處理函式名稱。

### <a name="remarks"></a>備註

更新訊息處理常式會更新與命令相關聯的功能表項目和工具列按鈕的狀態。 識別碼的範圍會以 *id1* 開頭，並以 *id2*結尾。

訊息對應範圍沒有自動支援，因此您必須自行放置宏。

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="on_control_range"></a><a name="on_control_range"></a> ON_CONTROL_RANGE

使用這個宏可將連續範圍的控制項識別碼對應到指定 Windows 通知訊息的單一訊息處理常式函數，例如 BN_CLICKED。

### <a name="syntax"></a>語法

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*wNotifyCode*<br/>
您的處理常式回應的通知碼。

*id1*<br/>
連續控制識別碼範圍開頭的命令識別碼。

*id2*<br/>
連續控制識別碼範圍結尾的命令識別碼。

*memberFxn*<br/>
控制項所對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

識別碼的範圍會以 *id1* 開頭，並以 *id2*結尾。 針對來自任何已對應控制項的指定通知呼叫處理常式。

訊息對應範圍沒有自動支援，因此您必須自行放置宏。

如需有關如何針對某個範圍的控制項識別碼來執行處理常式函式的詳細資訊，請參閱 [訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxmsg_。h

## <a name="see-also"></a>另請參閱

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006：訊息對應](../tn006-message-maps.md)<br/>
[COleCmdUI 類別](colecmdui-class.md)<br/>
[COleServerDoc：： OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[使用者定義的處理常式](user-defined-handlers.md)<br/>
[CCmdUI 類別](ccmdui-class.md)
