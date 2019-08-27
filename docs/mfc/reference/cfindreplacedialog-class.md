---
title: CFindReplaceDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 71234adec214bcbf5d42090edb582a7e5dd552b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506532"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 類別

可讓您在應用程式中實作為標準字串的 [尋找/取代] 對話方塊。

## <a name="syntax"></a>語法

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|呼叫此函式以建立`CFindReplaceDialog`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|建立並顯示`CFindReplaceDialog`對話方塊。|
|[CFindReplaceDialog::FindNext](#findnext)|呼叫此函式可判斷使用者是否想要尋找下一個出現的尋找字串。|
|[CFindReplaceDialog::GetFindString](#getfindstring)|呼叫此函式可取得目前的尋找字串。|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|呼叫此函式可在`FINDREPLACE`您已註冊的訊息處理常式中, 取得結構。|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|呼叫此函式可取得目前的取代字串。|
|[CFindReplaceDialog::IsTerminating](#isterminating)|呼叫此函式可判斷對話方塊是否正在終止。|
|[CFindReplaceDialog::MatchCase](#matchcase)|呼叫此函式可判斷使用者是否想要完全符合尋找字串的大小寫。|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|呼叫此函式可判斷使用者是否只想要比對整個單字。|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|呼叫此函式可判斷使用者是否想要取代所有出現的字串。|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|呼叫此函式可判斷使用者是否想要取代目前的文字。|
|[CFindReplaceDialog::SearchDown](#searchdown)|呼叫此函式可判斷使用者是否想要以向下方向進行搜尋。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|用來自訂`CFindReplaceDialog`物件的結構。|

## <a name="remarks"></a>備註

不同于其他的 windows 通用對話方塊, `CFindReplaceDialog`物件是無狀態的, 可讓使用者在螢幕上與其他視窗互動。 `CFindReplaceDialog`物件有兩種:尋找對話方塊和尋找/取代對話方塊。 雖然對話方塊可讓使用者輸入搜尋和搜尋/取代字串, 但不會執行任何搜尋或取代函式。 您必須將這些新增至應用程式。

若要建立`CFindReplaceDialog`物件, 請使用所提供的函式 (沒有引數)。 因為這是非強制回應對話方塊, 所以請使用**new**運算子 (而不是堆疊) 來配置堆積上的物件。

一旦建立`CFindReplaceDialog`物件之後, 您必須呼叫[create](#create)成員函式來建立和顯示對話方塊。

呼叫`Create`之前, 請先使用[m_fr](#m_fr)結構來初始化對話方塊。 結構的型別為[FINDREPLACE。](/windows/win32/api/commdlg/ns-commdlg-findreplacew) `m_fr` 如需此結構的詳細資訊, 請參閱 Windows SDK。

為了讓父視窗收到「尋找/取代」要求的通知, 您必須使用 Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函式, 並在處理此已註冊訊息的框架視窗中使用[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)訊息對應宏。

您可以判斷使用者是否已決定使用`IsTerminating`成員函式來終止對話方塊。

`CFindReplaceDialog`依賴 COMMDLG。Windows 3.1 和更新版本隨附的 DLL 檔案。

若要自訂對話方塊、從`CFindReplaceDialog`衍生類別, 請提供自訂對話方塊範本, 並加入訊息對應以處理來自擴充控制項的通知訊息。 任何未處理的訊息都應該傳遞至基類。

不需要自訂攔截函數。

如需使用`CFindReplaceDialog`的詳細資訊, 請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>需求

**標頭:** afxdlgs。h

##  <a name="cfindreplacedialog"></a>CFindReplaceDialog:: CFindReplaceDialog

建構 `CFindReplaceDialog` 物件。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>備註

因為物件是非強制回應對話方塊, 所以您必須使用 new 運算子在堆積上進行構造。 `CFindReplaceDialog`

在銷毀期間, 架構會嘗試在對話方塊的指標上執行**刪除**。 如果您已在堆疊上建立對話方塊, 則**此**指標不存在, 而且可能會導致未定義的行為。

如需有關`CFindReplaceDialog`物件結構的詳細資訊, 請參閱[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)總覽。 使用[CFindReplaceDialog:: Create](#create)成員函式來顯示對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>CFindReplaceDialog:: Create

視的值`bFindDialogOnly`而定, 建立並顯示 [尋找] 或 [尋找/取代] 對話方塊物件。

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*bFindDialogOnly*<br/>
將此參數設定為 [TRUE], 以顯示 [**尋找**] 對話方塊。 將它設定為 FALSE, 以顯示 [**尋找/取代**] 對話方塊。

*lpszFindWhat*<br/>
對話方塊出現時的預設搜尋字串指標。 如果是 Null, 對話方塊就不會包含預設的搜尋字串。

*lpszReplaceWith*<br/>
對話方塊出現時的預設取代字串的指標。 如果是 Null, 對話方塊就不會包含預設的取代字串。

*dwFlags*<br/>
一或多個旗標, 可供您用來自訂對話方塊的設定, 並使用位 OR 運算子進行結合。 預設值為 FR_DOWN, 指定搜尋是以向下方向繼續進行。 如需這些旗標的詳細資訊, 請參閱 Windows SDK 中的[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。 這是將會收到特殊訊息的視窗, 指出已要求尋找/取代動作。 如果是 Null, 則會使用應用程式的主視窗。

### <a name="return-value"></a>傳回值

如果成功建立對話方塊物件, 則為非零;否則為0。

### <a name="remarks"></a>備註

為了讓父視窗收到「尋找/取代」要求的通知, 您必須使用 Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函式, 其傳回值為應用程式實例特有的訊息編號。 您的框架視窗應該會有一個訊息對應專案, 宣告回呼函`OnFindReplace`式 (在接下來的範例中), 以處理這個已註冊的訊息。 下列程式碼片段是如何針對名`CMyRichEditView`為的框架視窗類別執行此動作的範例:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

在您`OnFindReplace`的函式內, 您可以使用[CFindReplaceDialog:: FindNext](#findnext)和[CFindReplaceDialog:: IsTerminating](#isterminating)方法來解讀使用者的意圖, 並建立用於尋找/取代作業的程式碼。

### <a name="example"></a>範例

  請參閱[CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)的範例。

##  <a name="findnext"></a>CFindReplaceDialog:: FindNext

從您的回呼函式呼叫此函式, 以判斷使用者是否想要尋找下一個出現的搜尋字串。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要尋找下一個出現的搜尋字串, 則為非零值;否則為0。

##  <a name="getfindstring"></a>CFindReplaceDialog:: GetFindString

從您的回呼函式呼叫此函式, 以取得要尋找的預設字串。

```
CString GetFindString() const;
```

### <a name="return-value"></a>傳回值

要尋找的預設字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>CFindReplaceDialog:: GetNotifier

呼叫此函式可取得目前 [尋找取代] 對話方塊的指標。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>參數

*lParam*<br/>
傳遞至框架視窗`OnFindReplace`成員函式的 lparam 值。

### <a name="return-value"></a>傳回值

目前對話方塊的指標。

### <a name="remarks"></a>備註

它應該在回呼函式中用來存取目前的對話方塊、呼叫其成員函式, 以及存取`m_fr`結構。

### <a name="example"></a>範例

如需如何註冊 OnFindReplace 處理常式以從 [尋找取代] 對話方塊接收通知的範例, 請參閱[CFindReplaceDialog:: Create](#create) 。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>CFindReplaceDialog:: GetReplaceString

呼叫此函式可取得目前的取代字串。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>傳回值

要用來取代找到的字串的預設字串。

### <a name="example"></a>範例

  請參閱[CFindReplaceDialog:: GetFindString](#getfindstring)的範例。

##  <a name="isterminating"></a>CFindReplaceDialog:: IsTerminating

在回呼函式中呼叫此函式, 以判斷使用者是否已決定終止對話方塊。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>傳回值

如果使用者已決定終止對話方塊, 則為非零值。否則為0。

### <a name="remarks"></a>備註

如果此函式傳回非零值, 您`DestroyWindow`應該呼叫目前對話方塊的成員函式, 並將任何對話方塊指標變數設定為 Null。 (選擇性) 您也可以儲存最後輸入的尋找/取代文字, 並使用它來初始化下一個 [尋找/取代] 對話方塊。

### <a name="example"></a>範例

  請參閱[CFindReplaceDialog:: GetFindString](#getfindstring)的範例。

##  <a name="m_fr"></a>CFindReplaceDialog:: m_fr

用來自訂`CFindReplaceDialog`物件。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>備註

`m_fr`是[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)類型的結構。 其成員會儲存對話方塊物件的特性。 在建立`CFindReplaceDialog`物件之後, 您可以使用`m_fr`來修改對話方塊中的各種值。

如需此結構的詳細資訊, 請`FINDREPLACE`參閱 Windows SDK 中的結構。

### <a name="example"></a>範例

  請參閱[CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)的範例。

##  <a name="matchcase"></a>CFindReplaceDialog:: MatchCase

呼叫此函式可判斷使用者是否想要完全符合尋找字串的大小寫。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要尋找完全符合搜尋字串案例的搜尋字串出現次數, 則為非零值;否則為0。

##  <a name="matchwholeword"></a>CFindReplaceDialog:: MatchWholeWord

呼叫此函式可判斷使用者是否只想要比對整個單字。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>傳回值

如果使用者只想要比對搜尋字串的整個單字, 則為非零。否則為0。

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

呼叫此函式可判斷使用者是否想要取代所有出現的字串。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>傳回值

如果使用者要求所有符合取代字串的字串都已被取代, 則為非零。否則為0。

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

呼叫此函式可判斷使用者是否想要取代目前的文字。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>傳回值

如果使用者要求以取代字串取代目前選取的字串, 則為非零值;否則為0。

##  <a name="searchdown"></a>CFindReplaceDialog:: SearchDown

呼叫此函式可判斷使用者是否想要以向下方向進行搜尋。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要以向下方向進行搜尋, 則為非零。0, 表示使用者想要以向上方向進行搜尋。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
