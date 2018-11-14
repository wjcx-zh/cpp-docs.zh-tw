---
title: 訊息對應巨集 (MFC)
ms.date: 11/04/2016
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
ms.openlocfilehash: 4012f1f0729ff0f46a8504c44f27a37cd55c77e5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327443"
---
# <a name="message-map-macros-mfc"></a>訊息對應巨集 (MFC)

若要支援訊息對應，MFC 提供下列巨集：

### <a name="message-map-declaration-and-demarcation-macros"></a>訊息對應宣告和分界巨集

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|宣告的訊息對應會使用類別將訊息與函式對應 (必須在類別宣告中使用)。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|開始進行訊息對應的定義 (必須在類別實作中使用)。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_interface_map)|開始定義數量包含單一樣板引數的類別類型上的訊息對應。 |
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
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|指出哪些更新處理常式會處理前兩個 pa 中指定的命令識別碼範圍] rameters 巨集。|
|[ON_CONTROL_RANGE](#on_control_range)|指出哪些函式會處理來自在巨集的第二和第三個參數中指定之控制項 ID 範圍的通知。 控制項通知訊息，例如 BN_CLICKED 為第一個參數。|

如需有關訊息對應、 訊息對應宣告和分界巨集和訊息對應巨集的詳細資訊，請參閱[訊息對應](../../mfc/reference/message-maps-mfc.md)並[訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。 如需訊息對應範圍的詳細資訊，請參閱[訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。

## <a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

開始您的訊息對應的定義。

### <a name="syntax"></a>語法

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定的訊息對應的類別名稱。

*baseClass*<br/>
指定的基底類別的名稱*theClass*。

### <a name="remarks"></a>備註

在實作 (.cpp) 檔案中定義您的類別成員函式，啟動訊息對應 BEGIN_MESSAGE_MAP 巨集，則每個訊息處理常式函式，新增巨集項目和完成 END_MESSAGE_MAP 使用訊息對應巨集。

如需訊息對應的詳細資訊，請參閱[訊息對應](message-maps-mfc.md)

### <a name="example"></a>範例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

開始定義數量包含單一樣板引數的類別類型上的訊息對應。

### <a name="syntax"></a>語法

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定的訊息對應的類別名稱。

*type_name*<br/>
指定類別的範本參數的名稱。

*baseClass*<br/>
指定的基底類別的名稱*theClass*。

### <a name="remarks"></a>備註

這個巨集就類似於[BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map)巨集; 不過，這個巨集適用於包含單一樣板引數的類別。

在您的類別的方法實作區段，開始訊息對應 BEGIN_TEMPLATE_MESSAGE_MAP 巨集;然後以您平常的標準訊息對應，請針對每個訊息處理常式方法加入巨集項目。 BEGIN_MESSAGE_MAP 巨集完成範本訊息地圖[END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map)巨集。

如需有關如何實作樣板類別的訊息對應的詳細資訊，請參閱[如何： 建立樣板類別的訊息對應](../how-to-create-a-message-map-for-a-template-class.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP

宣告此類別會定義訊息對應。 每個`CCmdTarget`-在您的程式中的衍生的類別必須提供處理訊息的訊息對應。

### <a name="syntax"></a>語法

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>備註

在類別宣告結尾使用 DECLARE_MESSAGE_MAP 巨集。 接著，在定義類別的成員函式的.cpp 檔案，使用 BEGIN_MESSAGE_MAP 巨集、 巨集項目為每個訊息處理常式函式和 END_MESSAGE_MAP 巨集。

> [!NOTE]
>  如果您之後 DECLARE_MESSAGE_MAP 宣告任何成員，您必須指定新的存取類型 (**公開**，**私人**，或**保護**) 它們。

如需有關訊息對應和 DECLARE_MESSAGE_MAP 巨集的詳細資訊，請參閱[訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="end_message_map"></a>  END_MESSAGE_MAP

結束訊息對應的定義。

### <a name="syntax"></a>語法

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>備註

如需有關訊息對應和 END_MESSAGE_MAP 巨集的詳細資訊，請參閱[訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="on_command"></a>  ON_COMMAND

這個巨集對應的成員函式的命令訊息。

### <a name="syntax"></a>語法

```
ON_COMMAND( id, memberFxn )
```

### <a name="parameters"></a>參數

*id*<br/>
命令 ID。

*memberFxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

指出哪些函式會處理命令訊息，從命令的使用者介面物件，例如功能表項目或工具列按鈕。

ON_COMMAND 當命令目標物件接收 Windows WM_COMMAND 訊息具有指定識別碼時，會呼叫此成員函式`memberFxn`以處理訊息。

您可以使用 ON_COMMAND，成員函式對應單一命令。 使用[ON_COMMAND_RANGE](#on_command_range)來將一組命令 id 對應至一個成員函式。 只有一個訊息對應項目可以比對指定的命令識別碼。也就是說，您無法將命令對應至一個以上的處理常式。 如需詳細資訊和範例，請參閱 <<c0> [ 訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>需求

**標頭：** afxmsg_.h

## <a name="on_command_ex"></a>  ON_COMMAND_EX

擴充命令處理常式成員函式。

### <a name="syntax"></a>語法

```
ON_COMMAND_EX(id, memberFxn);
```

### <a name="parameters"></a>參數

*id*<br/>
命令 ID。

*memberFxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

擴充的格式的命令訊息處理常式可供進階使用。 ON_COMMAND_EX 巨集用於這類訊息處理常式，並提供的超集合[ON_COMMAND](message-map-macros-mfc.md#on_command)功能。 擴充的命令處理常式成員函式會採用單一參數，包含命令 ID，UINT，並傳回 BOOL。 傳回的值應為 TRUE，表示已處理的命令;否則路由會繼續其他命令目標物件。

如需詳細資訊，請參閱 < 技術提示 [TN006： 訊息對應] tm006-訊息-maps.md)。

### <a name="requirements"></a>需求

標頭檔： afxmsg_.h

### <a name="see-also"></a>另請參閱

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006：訊息對應](../tn006-message-maps.md)

## <a name="on_control"></a>  ON_CONTROL

指出哪些函式會處理自訂控制項通知訊息。

### <a name="syntax"></a>語法

```
ON_CONTROL( wNotifyCode, id, memberFxn )
```

### <a name="parameters"></a>參數

*wNotifyCode*<br/>
控制項通知碼。

*id*<br/>
命令 ID。

*memberFxn*<br/>
命令對應的訊息處理函式名稱。

### <a name="remarks"></a>備註

控制項通知訊息是從控制項傳送至其父視窗。

應該只有一個 ON_CONTROL 巨集陳述式，在您的每一個都必須對應至訊息處理常式函式的控制項通知訊息的訊息對應中。

如需詳細資訊和範例，請參閱 <<c0> [ 訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>需求

**標頭：** afxmsg_.h

## <a name="on_message"></a>  ON_MESSAGE

指出哪些函式會處理使用者定義的訊息。

### <a name="syntax"></a>語法

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>參數

*message*<br/>
訊息 ID。

*memberFxn*<br/>
訊息所對應的訊息處理常式函式的名稱。

函式的類型必須是`afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`。

### <a name="remarks"></a>備註

使用者定義的訊息會顯示標準 Windows WM_MESSAGE 郵件沒有任何訊息。 選取時的訊息識別碼，您必須使用 0x7FFF 或 WM_APP (0x8000) 範圍 」 的 (0x0400) WM_USER 內的值來 0xBFFF。 如需訊息識別碼的詳細資訊，請參閱[WM_APP](/windows/desktop/winmsg/wm-app)。

應該只有一個 ON_MESSAGE 巨集陳述式，在您的每一個都必須對應至訊息處理常式函式的使用者定義訊息的訊息對應中。

> [!NOTE]
>  使用者定義的訊息，除了 ON_MESSAGE 會處理較不常見的 Windows 訊息。 如需詳細資訊，請參閱 <<c0> [ 訊息對應](../../mfc/tn006-message-maps.md)。

如需詳細資訊和範例，請參閱 <<c0> [ 訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)和[使用者定義的處理常式](user-defined-handlers.md)

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

**標頭：** afxmsg_.h

## <a name="on_olecmd"></a>  ON_OLECMD

將命令路由傳送命令分派介面透過`IOleCommandTarget`。

### <a name="syntax"></a>語法

```
ON_OLECMD( pguid, olecmdid, id )
```

### <a name="parameters"></a>參數

*pguid*<br/>
此命令屬於哪個命令群組的識別碼。 標準群組會使用 NULL。

*olecmdid*<br/>
OLE 命令識別碼。

*id*<br/>
功能表識別碼、 工具列 ID、 按鈕 ID 或其他資源或物件發出命令的識別碼。

### <a name="remarks"></a>備註

`IOleCommandTarget` 允許容器接收命令是源自於 DocObject 使用者介面，並可讓容器傳送相同的命令 (例如新增、 開啟、 另存新檔和在 [檔案] 功能表中，列印和複製、 貼上、 復原，依此類推 [編輯] 功能表) 以 DocObject。

`IOleCommandTarget` OLE Automation 的比簡單`IDispatch`。 `IOleCommandTarget` 完全依賴一組標準的命令也很少具有引數，並牽涉到任何型別資訊 （型別安全就會受到影響的命令引數）。 如果您需要將分派引數的命令，使用[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)。

`IOleCommandTarget`標準功能表命令已由 MFC 實作中的下列巨集：

**ON_OLECMD_CLEARSELECTION （)**

分派清除編輯命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY （)**

分派編輯複製命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT （)**

分派編輯剪下 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW （)**

分派開新檔案的命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN （)**

將分派檔案開啟的命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP （)**

將分派檔案 [版面設定] 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE （)**

分派編輯貼上 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL （)**

分派編輯選擇性貼上命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT （)**

將分派檔案列印命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW （)**

將分派檔案預覽列印 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO （)**

分派編輯重做命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE （)**

分派儲存檔案的命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS （)**

將分派檔案另存新檔 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS （)**

分派副本存新檔 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL （)**

分派編輯選取的所有命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO （)**

分派編輯 Undo 命令。 實作為：

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>需求

**標頭：** afxdocob.h

### <a name="see-also"></a>另請參閱

[COleCmdUI 類別](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE

Windows`RegisterWindowMessage`函式用來定義新的視窗訊息，保證是唯一在整個系統。

### <a name="syntax"></a>語法

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>參數

*nMessageVariable*<br/>
已註冊的視窗訊息 ID 變數中。

*memberFxn*<br/>
訊息所對應的訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

這個巨集指出哪些函式會處理已註冊的訊息。

如需詳細資訊和範例，請參閱 <<c0> [ 訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>範例

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>需求

**標頭：** afxmsg_.h

### <a name="see-also"></a>另請參閱

[RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947)<br/>
[使用者定義的處理常式](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>  ON_REGISTERED_THREAD_MESSAGE

指出哪些函式會處理 Windows RegisterWindowMessage 函式所註冊的訊息。

### <a name="syntax"></a>語法

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>參數

*nMessageVariable*<br/>
已註冊的視窗訊息 ID 變數中。

*memberFxn*<br/>
訊息所對應至 CWinThread 訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

RegisterWindowMessage 用來定義新的視窗訊息，保證是唯一在整個系統。 當您有 CWinThread 類別時，必須使用 ON_REGISTERED_THREAD_MESSAGE 而不是 ON_REGISTERED_MESSAGE。

### <a name="requirements"></a>需求

**標頭：** afxmsg_.h

## <a name="on_thread_message"></a>  ON_THREAD_MESSAGE

指出哪些函式會處理使用者定義的訊息。

### <a name="syntax"></a>語法

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>參數

*message*<br/>
訊息 ID。

*memberFxn*<br/>
名稱`CWinThread`-訊息-訊息所對應的處理常式函式。

### <a name="remarks"></a>備註

ON_THREAD_MESSAGE 必須使用而不是 ON_MESSAGE，當您有`CWinThread`類別。 使用者定義的訊息會顯示標準 Windows WM_MESSAGE 郵件沒有任何訊息。 應該只有一個 ON_THREAD_MESSAGE 巨集陳述式，在您的每一個都必須對應至訊息處理常式函式的使用者定義訊息的訊息對應中。

### <a name="requirements"></a>需求

**標頭：** afxole.h

## <a name="on_update_command_ui"></a>  ON_UPDATE_COMMAND_UI

這個巨集指出哪些函式會處理使用者介面更新命令訊息。

### <a name="syntax"></a>語法

```
ON_UPDATE_COMMAND_UI( id, memberFxn )
```

### <a name="parameters"></a>參數

*id*<br/>
訊息 ID。

*memberFxn*<br/>
訊息所對應的訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

應該為每個都必須對應至訊息處理常式函式的使用者介面更新命令訊息對應中的一個 ON_UPDATE_COMMAND_UI 巨集陳述式。

如需詳細資訊和範例，請參閱 <<c0> [ 訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>需求

**標頭：** afxole.h

### <a name="see-also"></a>另請參閱

[CCmdUI 類別](ccmdui-class.md)

## <a name="on_command_range"></a>  ON_COMMAND_RANGE

您可以使用這個巨集，將連續範圍的命令 Id 對應至單一訊息處理常式函式。

### <a name="syntax"></a>語法

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*id1*<br/>
命令 Id 的連續範圍的開頭的命令識別碼。

*id2*<br/>
結尾的連續範圍的命令 Id 的命令識別碼。

*memberFxn*<br/>
命令所對應的訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

範圍的識別碼開頭*id1* ，並結束*id2*。

ON_COMMAND_RANGE 可用於將一連串的命令 Id 對應至一個成員函式。 使用[ON_COMMAND](#on_command)對應的成員函式的單一命令。 只有一個訊息對應項目可比對指定的命令識別碼。 也就是說，您無法將命令對應至一個以上的處理常式。 如需有關對應訊息範圍的詳細資訊，請參閱[訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。

沒有任何自動式支援訊息對應範圍，因此您必須自行將巨集。

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

**標頭：** afxmsg_.h

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE

將連續範圍的命令 Id 對應至單一更新訊息處理常式函式中。

### <a name="syntax"></a>語法

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*id1*<br/>
命令 Id 的連續範圍的開頭的命令識別碼。

*id2*<br/>
結尾的連續範圍的命令 Id 的命令識別碼。

*memberFxn*<br/>
命令所對應的更新訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

更新訊息處理常式更新功能表項目和工具列按鈕與命令相關聯的狀態。 範圍的識別碼開頭*id1* ，並結束*id2*。

沒有任何自動式支援訊息對應範圍，因此您必須自行將巨集。

### <a name="requirements"></a>需求

**標頭：** afxmsg_.h

## <a name="on_control_range"></a>  ON_CONTROL_RANGE

您可以使用這個巨集，將控制項 Id 的連續範圍對應至指定的 Windows 通知訊息，例如 BN_CLICKED 的單一訊息處理常式函式。

### <a name="syntax"></a>語法

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>參數

*wNotifyCode*<br/>
您的處理常式回應的通知程式碼。

*id1*<br/>
控制項 Id 的連續範圍的開頭的命令識別碼。

*id2*<br/>
結尾的連續範圍的控制項 Id 的命令識別碼。

*memberFxn*<br/>
控制項所對應的訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

範圍的識別碼開頭*id1* ，並結束*id2*。 處理常式會呼叫指定的通知來自任何對應的控制項。

沒有任何自動式支援訊息對應範圍，因此您必須自行將巨集。

如需有關如何實作某個範圍內的控制項 Id 的處理常式函式的詳細資訊，請參閱[訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。

### <a name="requirements"></a>需求

**標頭：** afxmsg_.h
