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
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373848"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 類別

允許您在應用程式中實現標準字串"尋找"對話框。

## <a name="syntax"></a>語法

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFind 取代對話框::C尋找取代對話框](#cfindreplacedialog)|呼叫此函式以建構物件`CFindReplaceDialog`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFind 取代對話框::建立](#create)|創建並顯示`CFindReplaceDialog`對話方塊。|
|[CFind 替換對話框::尋找下一個](#findnext)|呼叫此函數以確定使用者是否希望查找尋找字串的下一個匹配項。|
|[CFind 取代對話框::抓取搜尋字串](#getfindstring)|呼叫此函數以檢索目前尋找字串。|
|[CFind 取代對話框::取得指示器](#getnotifier)|調用此函數以檢索已`FINDREPLACE`註冊的消息處理程式中的結構。|
|[CFind 取代對話框::取得替換字串](#getreplacestring)|呼叫此函數以檢索當前替換字串。|
|[CFind 取代對話框::正在終結](#isterminating)|調用此函數以確定對話方塊是否終止。|
|[CFind 替換對話框::匹配案例](#matchcase)|呼叫此函數以確定使用者是否要完全匹配查找字串的情況。|
|[CFind 取代對話框::符合完整字](#matchwholeword)|調用此函數以確定使用者是否只想匹配整個單詞。|
|[CFind 取代對話框::全部取代](#replaceall)|呼叫此函數以確定使用者是否希望替換字串的所有匹配項。|
|[CFind 取代對話框::取代電流](#replacecurrent)|調用此函數以確定使用者是否希望替換當前單詞。|
|[CFind 取代對話框::搜尋向下](#searchdown)|調用此函數以確定使用者是否希望搜索朝向下方向進行。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFind 替換對話框::m_fr](#m_fr)|定義物件的結構`CFindReplaceDialog`。|

## <a name="remarks"></a>備註

與其他 Windows 常見對話框`CFindReplaceDialog`不同, 對像是無模式的,允許使用者在螢幕上與其他窗互。 有兩種`CFindReplaceDialog`物件:尋找對話框和搜尋/替換對話框。 儘管對話框允許使用者輸入搜索和搜索/替換字串,但它們不執行任何搜索或替換函數。 您必須將這些添加到應用程式中。

要建構物件`CFindReplaceDialog`,請使用提供的構造函數(沒有參數)。 由於這是一個無模式對話方塊,請使用**新**運算符而不是堆疊上分配物件。

建構`CFindReplaceDialog`物件後,必須調用[「創建](#create)成員」函數以創建並顯示對話方塊。

使用[m_fr](#m_fr)結構在`Create`調用 之前初始化對話方塊。 結構`m_fr`為[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)類型。 有關此結構的詳細資訊,請參閱 Windows SDK。

為了通知父視窗查找/替換請求,必須使用 Windows[註冊視窗訊息](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)功能,並在框架視窗中使用處理此已註冊消息的幀視窗中[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)消息映射宏。

您可以確定使用者是否已決定終止具有成員函數的`IsTerminating`對話方塊。

`CFindReplaceDialog`依賴於 COMMDLG。隨 Windows 版本 3.1 及更高版本一起附帶的 DLL 檔。

要自定義對話框,請從`CFindReplaceDialog`派生類,並提供自定義對話框範本,並添加消息映射來處理來自擴展控制項的通知消息。 任何未處理的消息都應傳遞到基類。

不需要自定義挂鉤功能。

有關`CFindReplaceDialog`使用的詳細資訊,請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFind 取代對話框::C尋找取代對話框

建構 `CFindReplaceDialog` 物件。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>備註

由於`CFindReplaceDialog`對象是無模式對話框,因此必須使用**新**運算符在堆上構造它。

在銷毀期間,框架嘗試對對話框的指標執行**刪除。** 如果在堆疊上創建了對話框,**則此**指標不存在,並且可能會導致未定義的行為。

有關`CFindReplaceDialog`物件構造的詳細資訊,請參閱[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概述。 使用[CFind 替換對話框:創建](#create)成員函數來顯示對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFind 取代對話框::建立

建立並顯示「尋找」或「尋找/取代」對話框物件,具體取決於的值`bFindDialogOnly`。

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*b 只尋找對話*<br/>
將此參數設定為 TRUE 以顯示 **「搜尋」** 對話框。 將其設定為 FALSE 以顯示 **「尋找/取代**」對話框。

*lpszFind什麼*<br/>
顯示對話框時指向預設搜尋字串的指標。 如果為 NULL,則對話方塊不包含預設搜尋字串。

*lpsz 取代與*<br/>
當對話框出現時指向預設替換字串的指標。 如果為 NULL,則對話方塊不包含預設取代字串。

*dwFlags*<br/>
可以使用一個或多個標誌自定義對話框的設置,使用位或運算符組合使用。 默認值為FR_DOWN,它指定搜索要朝向下方向進行。 有關這些標誌的詳細資訊,請參閱 Windows SDK 中的[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)結構。

*pparentwnd*<br/>
指向對話框的父視窗或所有者視窗的指標。 這是將接收指示請求查找/替換操作的特殊消息的視窗。 如果 NULL,則使用應用程式的主視窗。

### <a name="return-value"></a>傳回值

如果成功創建了對話框物件,則非零;否則 0。

### <a name="remarks"></a>備註

為了通知父視窗查找/替換請求,必須使用 Windows[註冊視窗消息](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函數,其返回值是應用程式實例唯一的消息編號。 幀窗口應具有消息映射條目,該條目聲明處理此已註冊消息的`OnFindReplace`回調函數(在以下示例中)。 以下片段是如何針對名為`CMyRichEditView`的畫面視窗類別執行此操作的範例:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

在函數`OnFindReplace`中,您可以使用[CFindReplaceDialog::FindReplaceDialog:FindNext](#findnext)和[CFindReplaceDialog::即終止](#isterminating)方法來解釋使用者的意圖,併為查找/替換操作創建代碼。

### <a name="example"></a>範例

  請參考[CFind 取代對話框的範例:cFind 取代對話框](#cfindreplacedialog)。

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFind 替換對話框::尋找下一個

從回調函數調用此函數以確定使用者是否希望查找搜索字串的下一個匹配項。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要查找搜索字串的下一個匹配項,則非零;否則 0。

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFind 取代對話框::抓取搜尋字串

從回調函數調用此函數以檢索要查找的預設字串。

```
CString GetFindString() const;
```

### <a name="return-value"></a>傳回值

要查找的預設字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFind 取代對話框::取得指示器

呼叫此函數以檢索指向當前"尋找"對話框的指標。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>參數

*lParam*<br/>
傳遞到框架視窗的成員函數的`OnFindReplace` *lparam*值。

### <a name="return-value"></a>傳回值

指向當前對話框的指標。

### <a name="remarks"></a>備註

應在回調函數中使用它來訪問當前對話框、調用其成員函數和訪問`m_fr`結構。

### <a name="example"></a>範例

請參閱[CFindReplaceDialog::建立](#create)有關如何註冊 OnFindReplace 處理程式以接收來自「查找取代」對話框的通知的範例。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFind 取代對話框::取得替換字串

呼叫此函數以檢索當前替換字串。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>傳回值

要取代找到的字串的預設字串。

### <a name="example"></a>範例

  請參考[CFind 取代對話框的範例:抓取此字串](#getfindstring)。

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFind 取代對話框::正在終結

在回調函數中調用此函數以確定使用者是否已決定終止該對話方塊。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>傳回值

如果用戶決定終止該對話框,則為非零;否則 0。

### <a name="remarks"></a>備註

如果此函數返回非零,則應調用當前對話框`DestroyWindow`的成員函數,並將任何對話框指標變數設置為 NULL。 或者,您還可以存儲上次輸入的查找/替換文本,並用它來初始化下一個尋找/替換對話框。

### <a name="example"></a>範例

  請參考[CFind 取代對話框的範例:抓取此字串](#getfindstring)。

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFind 替換對話框::m_fr

用於自定義`CFindReplaceDialog`物件。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>備註

`m_fr`是[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)類型的結構。 其成員存儲對話框物件的特徵。 建構`CFindReplaceDialog`物件后,可以`m_fr`使用 修改對話框中的各種值。

有關此結構的詳細資訊,請參閱 Windows `FINDREPLACE` SDK 中的結構。

### <a name="example"></a>範例

  請參考[CFind 取代對話框的範例:cFind 取代對話框](#cfindreplacedialog)。

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFind 替換對話框::匹配案例

呼叫此函數以確定使用者是否要完全匹配查找字串的情況。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要查找與搜索字串的情況完全匹配的搜索字串的匹配項,則非零;否則 0。

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFind 取代對話框::符合完整字

調用此函數以確定使用者是否只想匹配整個單詞。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>傳回值

如果使用者只想匹配搜索字串的整個單詞,則非零;否則 0。

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFind 取代對話框::全部取代

呼叫此函數以確定使用者是否希望替換字串的所有匹配項。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>傳回值

如果使用者請求替換與替換字串匹配的所有字串,則非零;否則 0。

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFind 取代對話框::取代電流

調用此函數以確定使用者是否希望替換當前單詞。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>傳回值

如果使用者請求將當前選定的字串替換為替換字串,則為非零;否則 0。

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFind 取代對話框::搜尋向下

調用此函數以確定使用者是否希望搜索朝向下方向進行。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>傳回值

如果使用者希望搜索朝向下方向進行,則非零;0 如果使用者希望搜索朝向上方向進行。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
