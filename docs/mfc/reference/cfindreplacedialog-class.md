---
title: CFindReplaceDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7948b755e65b3a64c57f2fd99cf4eefa68cb3cb9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432369"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 類別

可讓您在 您的應用程式中實作標準字串 尋找/取代 對話方塊。

## <a name="syntax"></a>語法

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|呼叫此函式來建構`CFindReplaceDialog`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|建立並顯示`CFindReplaceDialog` 對話方塊。|
|[CFindReplaceDialog::FindNext](#findnext)|呼叫此函式可判斷使用者是否要尋找尋找字串的下一個出現位置。|
|[CFindReplaceDialog::GetFindString](#getfindstring)|呼叫此函式可擷取目前的尋找字串。|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|呼叫此函式可擷取`FINDREPLACE`在已註冊的訊息處理常式中的結構。|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|呼叫此函式可擷取目前的取代字串。|
|[CFindReplaceDialog::IsTerminating](#isterminating)|呼叫此函式來判斷是否要結束對話方塊。|
|[CFindReplaceDialog::MatchCase](#matchcase)|呼叫此函式可判斷使用者是否想要完全符合尋找字串的大小寫。|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|呼叫此函式可判斷使用者是否要比對整個字相符。|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|呼叫此函式可判斷使用者是否想要取代之字串的所有項目。|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|呼叫此函式可判斷使用者是否想要取代目前的文字。|
|[CFindReplaceDialog::SearchDown](#searchdown)|呼叫此函式可判斷使用者是否想要繼續向下的方向搜尋。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|結構，用來自訂`CFindReplaceDialog`物件。|

## <a name="remarks"></a>備註

不同於其他 Windows 通用對話方塊，`CFindReplaceDialog`物件會非強制回應，讓使用者能夠與其他 windows 互動，而它們是在螢幕上。 有兩種類型的`CFindReplaceDialog`物件： 尋找對話方塊和 [尋找/取代] 對話方塊。 對話方塊可讓使用者輸入的搜尋，並搜尋/取代字串，雖然它們不會執行任何搜尋或取代函式。 您必須將這些應用程式。

若要建構`CFindReplaceDialog`物件，請使用提供的建構函式 （其有任何引數）。 由於這是強制回應對話方塊時，配置堆積上的物件**新**運算子，而不是在堆疊上。

一次`CFindReplaceDialog`在建構物件，您必須呼叫[建立](#create)成員函式來建立和顯示對話方塊。

使用[m_fr](#m_fr)結構，以初始化對話方塊中，然後再呼叫`Create`。 `m_fr`結構的類型是[FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)。 如需有關此結構的詳細資訊，請參閱 Windows SDK。

為了讓父視窗的 尋找/取代要求通知，您必須使用 Windows [RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947)函式，並使用[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)訊息對應巨集，在您的畫面格處理這個已註冊的訊息的視窗。

您可以判斷使用者是否已決定要終止的對話方塊`IsTerminating`成員函式。

`CFindReplaceDialog` 依賴 COMMDLG。隨附於 Windows 版本 3.1 和更新版本的 DLL 檔案。

若要自訂對話方塊中，衍生的類別`CFindReplaceDialog`、 提供自訂對話方塊範本，及新增的訊息對應來處理從擴充的控制項通知訊息。 任何未處理的訊息應傳遞至基底類別。

自訂攔截函式不需要。

如需有關使用`CFindReplaceDialog`，請參閱 <<c2> [ 通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs.h

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

建構 `CFindReplaceDialog` 物件。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>備註

因為`CFindReplaceDialog`物件為非強制回應對話方塊，您必須先將它在堆積上建構，利用**新**運算子。

在解構期間，架構會嘗試執行**刪除此**在對話方塊中的指標。 如果您在堆疊上，建立對話方塊**這**指標不存在，而且可能造成未定義的行為。

如需有關建構`CFindReplaceDialog`物件，請參閱[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概觀。 使用[CFindReplaceDialog::Create](#create)成員函式來顯示對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

建立並顯示 尋找 或 尋找/取代對話方塊物件，根據的值`bFindDialogOnly`。

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
將此參數設為 true，則顯示**尋找** 對話方塊。 將它設定為 FALSE，以顯示**尋找/取代** 對話方塊。

*lpszFindWhat*<br/>
當對話方塊出現時，才會進行預設搜尋字串的指標。 如果是 NULL，對話方塊不包含預設的搜尋字串。

*lpszReplaceWith*<br/>
當對話方塊出現時，才會進行預設值取代字串的指標。 如果是 NULL，對話方塊不包含預設的取代字串。

*dwFlags*<br/>
您可以使用自訂設定的對話方塊中，使用位元的 OR 運算子結合的一或多個標幟。 預設值是 FR_DOWN，指定是要繼續向下的方向搜尋。 請參閱[FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)如需有關這些旗標的 Windows SDK 中的結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。 這是將會收到指出要求 尋找/取代動作訊息的視窗。 如果是 NULL，則會使用應用程式的主視窗。

### <a name="return-value"></a>傳回值

已成功建立對話方塊物件; 如果為非零否則為 0。

### <a name="remarks"></a>備註

為了讓父視窗的 尋找/取代要求通知，您必須使用 Windows [RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947)函式的傳回值是應用程式的執行個體唯一的訊息數目。 框架視窗應該會有訊息對應項目宣告回呼函式 (`OnFindReplace`接下來的範例中) 可處理這個已註冊的訊息。 下列程式碼片段是如何執行這項操作，名為框架視窗類別的範例`CMyRichEditView`:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

在您`OnFindReplace`函式，您使用解譯的使用者是否同意[CFindReplaceDialog::FindNext](#findnext)及[CFindReplaceDialog::IsTerminating](#isterminating)方法和您建立的程式碼尋找/取代作業。

### <a name="example"></a>範例

  範例，請參閱[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

從您的回呼函式，來判斷使用者是否要搜尋字串的下一個呼叫此函式。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要搜尋的字串; 的下一個非零值否則為 0。

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

呼叫此函式，從您的回呼函式，以取得要尋找的預設字串。

```
CString GetFindString() const;
```

### <a name="return-value"></a>傳回值

要尋找的預設字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

呼叫此函式可擷取目前的尋找取代對話方塊中的指標。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>參數

*lParam*<br/>
*Lparam*值傳遞至框架視窗的`OnFindReplace`成員函式。

### <a name="return-value"></a>傳回值

到目前的對話方塊中的指標。

### <a name="remarks"></a>備註

應該在您的回呼函式中用來存取目前的對話方塊中，呼叫其成員函式和存取`m_fr`結構。

### <a name="example"></a>範例

請參閱[CFindReplaceDialog::Create](#create)如需如何註冊 OnFindReplace 處理常式，以接收通知，從 [尋找取代] 對話方塊中的範例。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

呼叫此函式可擷取目前的取代字串。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>傳回值

預設的字串，用來取代找到的字串。

### <a name="example"></a>範例

  範例，請參閱[CFindReplaceDialog::GetFindString](#getfindstring)。

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

呼叫此函式，在您的回呼函式，以判斷使用者是否已決定要終止的對話方塊。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>傳回值

如果使用者已決定要終止對話方塊中，為非零否則為 0。

### <a name="remarks"></a>備註

如果此函式傳回非零值，您應該呼叫`DestroyWindow`成員函式，[目前] 對話方塊的方塊，並將任何對話方塊指標變數設定為 NULL。 （選擇性） 您也可以儲存最後輸入的尋找/取代文字，並使用它來初始化 [下一步] 的 [尋找/取代] 對話方塊。

### <a name="example"></a>範例

  範例，請參閱[CFindReplaceDialog::GetFindString](#getfindstring)。

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

用來自訂`CFindReplaceDialog`物件。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>備註

`m_fr` 是一種結構的型別[FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)。 其成員儲存對話方塊物件的特性。 在建構之後`CFindReplaceDialog`物件，您可以使用`m_fr`修改在對話方塊中的各種值。

如需有關此結構的詳細資訊，請參閱`FINDREPLACE`Windows SDK 中的結構。

### <a name="example"></a>範例

  範例，請參閱[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

呼叫此函式可判斷使用者是否想要完全符合尋找字串的大小寫。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要尋找完全相符的搜尋字串，大小寫的搜尋字串的出現，非零值。否則為 0。

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

呼叫此函式可判斷使用者是否要比對整個字相符。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要比對整個文字搜尋字串; 的非零值否則為 0。

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

呼叫此函式可判斷使用者是否想要取代之字串的所有項目。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>傳回值

非零值，如果使用者已要求，取代所有相符的取代字串的字串;否則為 0。

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

呼叫此函式可判斷使用者是否想要取代目前的文字。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>傳回值

如果使用者已要求目前選取的字串，會取代在取代字串中，為非零否則為 0。

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

呼叫此函式可判斷使用者是否想要繼續向下的方向搜尋。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>傳回值

如果使用者想要向下的方向; 繼續進行搜尋，非零值。如果使用者想要繼續向上搜尋，0。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
