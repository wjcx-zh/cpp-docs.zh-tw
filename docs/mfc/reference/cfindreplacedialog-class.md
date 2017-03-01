---
title: "CFindReplaceDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFindReplaceDialog
dev_langs:
- C++
helpviewer_keywords:
- text searches, replacing text
- text searches, CFindReplaceDialog class
- Find/Replace dialog box
- replacing text, CFindReplaceDialog class
- CFindReplaceDialog class
- replacing text
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 510f6a763dbacb7d4e1b14ea808a4baaaf3d6bf3
ms.lasthandoff: 02/24/2017

---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 類別
可讓您在應用程式中實作標準字串 [尋找/取代] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|呼叫此函式來建構`CFindReplaceDialog`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|建立及顯示`CFindReplaceDialog`對話方塊。|  
|[CFindReplaceDialog::FindNext](#findnext)|呼叫此函式可判斷使用者是否想要尋找字串的下一個。|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|呼叫此函式可擷取目前的尋找字串。|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|呼叫此函式可擷取**FINDREPLACE**已註冊的訊息處理常式中的結構。|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|呼叫此函式可擷取目前的取代字串。|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|呼叫此函式可判斷是否已終止 對話方塊。|  
|[CFindReplaceDialog::MatchCase](#matchcase)|呼叫此函式可判斷使用者是否想要完全符合尋找字串的大小寫。|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|呼叫此函式可判斷使用者是否想要比對整個的文字。|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|呼叫此函式可判斷使用者是否想要被取代字串的所有項目。|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|呼叫此函式可判斷使用者是否想要取代目前的文字。|  
|[CFindReplaceDialog::SearchDown](#searchdown)|呼叫此函式可判斷使用者是否要繼續向下的方向搜尋。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|結構，用來自訂`CFindReplaceDialog`物件。|  
  
## <a name="remarks"></a>備註  
 不同於其他 Windows 通用對話方塊，`CFindReplaceDialog`物件為非強制回應，讓使用者能夠在螢幕上時，與其他 windows 互動。 有兩種類型的`CFindReplaceDialog`物件︰ 尋找對話方塊和 [尋找/取代] 對話方塊。 雖然對話方塊允許使用者輸入的搜尋，並搜尋或取代字串，但它們不執行任何搜尋或取代函式。 您必須將這些應用程式。  
  
 若要建構`CFindReplaceDialog`物件，請使用提供的建構函式 （它沒有任何引數）。 由於這是強制回應對話方塊時，配置堆積上的物件**新**運算子，而不是在堆疊上。  
  
 一次`CFindReplaceDialog`在建構物件，您必須呼叫[建立](#create)成員函式來建立和顯示對話方塊。  
  
 使用[m_fr](#m_fr)結構，以初始化對話方塊，然後再呼叫**建立**。 `m_fr`結構的型別是[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。 如需這個結構的詳細資訊，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 為了讓父視窗的 尋找/取代要求通知，您必須使用 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函式，並使用[ON_REGISTERED_MESSAGE](http://msdn.microsoft.com/library/93c1c068-ae8c-4e04-8a60-a603800ab57d)您處理這個已註冊的訊息的框架視窗中的訊息對應巨集。  
  
 您可以判斷使用者是否已決定要終止與對話方塊`IsTerminating`成員函式。  
  
 `CFindReplaceDialog`依賴 COMMDLG。隨附於 Windows 3.1 和更新版本的 DLL 檔案。  
  
 若要自訂對話方塊中，衍生自`CFindReplaceDialog`、 提供自訂的對話方塊範本，以及新增訊息對應到處理從擴充的控制項通知訊息。 任何未處理的訊息應該傳遞至基底類別。  
  
 自訂攔截函式不需要。  
  
 如需有關使用`CFindReplaceDialog`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdlgs.h  
  
##  <a name="a-namecfindreplacedialoga--cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog  
 建構 `CFindReplaceDialog` 物件。  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>備註  
 因為`CFindReplaceDialog`物件是強制回應對話方塊，您必須先將它在堆積上建構，使用`new`運算子。  
  
 在解構時，架構會嘗試執行`delete this`上 對話方塊中的指標。 如果您在堆疊上，建立對話方塊`this`指標不存在，可能會造成未定義的行為。  
  
 如需有關建構`CFindReplaceDialog`物件，請參閱[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概觀。 使用[CFindReplaceDialog::Create](#create)成員函式來顯示對話方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&170;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="a-namecreatea--cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog::Create  
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
 `bFindDialogOnly`  
 這個參數設定為`TRUE`顯示**尋找**對話方塊。 將它設定為`FALSE`顯示**尋找/取代**對話方塊。  
  
 `lpszFindWhat`  
 對話方塊出現時的預設搜尋字串的指標。 如果`NULL`，對話方塊不包含預設的搜尋字串。  
  
 `lpszReplaceWith`  
 對話方塊出現時的預設替代字串的指標。 如果`NULL`，對話方塊不包含預設值取代字串。  
  
 `dwFlags`  
 一或多個旗標可用於自訂對話方塊中，使用位元 OR 運算子合併的設定。 預設值是`FR_DOWN`，指定是要繼續向下的方向搜尋。 請參閱[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關這些旗標。  
  
 `pParentWnd`  
 對話方塊的父系或擁有者視窗的指標。 這是將會收到指出尋找/取代動作要求訊息的視窗。 如果`NULL`，使用應用程式的主視窗。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立對話方塊物件。否則為 0。  
  
### <a name="remarks"></a>備註  
 為了讓父視窗的 尋找/取代要求通知，您必須使用 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函式的傳回值是唯一的應用程式執行個體的訊息編號。 框架視窗應該會有訊息對應項目宣告回呼函式 (`OnFindReplace`接下來的範例中)，會處理已註冊的訊息。 下列程式碼片段是如何執行這項操作，名為框架視窗類別的範例`CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView #&171;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView #&172;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&173;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 在您`OnFindReplace`函式，使用解譯的使用者[CFindReplaceDialog::FindNext](#findnext)和[CFindReplaceDialog::IsTerminating](#isterminating)方法和您建立的尋找/取代作業的程式碼。  
  
### <a name="example"></a>範例  
  請參閱範例[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。  
  
##  <a name="a-namefindnexta--cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog::FindNext  
 若要判斷使用者是否想要搜尋字串的下一個回呼函數中呼叫此函式。  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果使用者想要搜尋的字串; 的下一個非零否則為 0。  
  
##  <a name="a-namegetfindstringa--cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog::GetFindString  
 呼叫此函式，從您的回呼函式，以取得要尋找的預設字串。  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>傳回值  
 要尋找的預設字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&69;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="a-namegetnotifiera--cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog::GetNotifier  
 呼叫此函式可擷取目前尋找取代 對話方塊的指標。  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `lParam`  
 **Lparam**值傳遞至框架視窗的**OnFindReplace**成員函式。  
  
### <a name="return-value"></a>傳回值  
 目前的對話方塊指標。  
  
### <a name="remarks"></a>備註  
 應該在您的回呼函式中用來存取目前的對話方塊，請呼叫其成員函式和存取`m_fr`結構。  
  
### <a name="example"></a>範例  
 請參閱[CFindReplaceDialog::Create](#create)如需如何註冊 OnFindReplace 處理常式，以尋找取代 對話方塊中收到通知的範例。  
  
 [!code-cpp[NVC_MFCDocView #&69;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="a-namegetreplacestringa--cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString  
 呼叫此函式可擷取目前的取代字串。  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>傳回值  
 預設的字串，用來取代找到的字串。  
  
### <a name="example"></a>範例  
  請參閱範例[CFindReplaceDialog::GetFindString](#getfindstring)。  
  
##  <a name="a-nameisterminatinga--cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog::IsTerminating  
 呼叫此函式回呼函式來判斷使用者是否已決定要終止的對話方塊內。  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果使用者已決定要結束此對話方塊。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此函數會傳回非零值，您應該呼叫`DestroyWindow`目前對話方塊和任何對話方塊指標變數的集合的成員函式**NULL**。 （選擇性） 您也可以儲存最後輸入的尋找/取代文字，並用來初始化 下一步的 尋找/取代 對話方塊。  
  
### <a name="example"></a>範例  
  請參閱範例[CFindReplaceDialog::GetFindString](#getfindstring)。  
  
##  <a name="a-namemfra--cfindreplacedialogmfr"></a><a name="m_fr"></a>CFindReplaceDialog::m_fr  
 用來自訂`CFindReplaceDialog`物件。  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>備註  
 `m_fr`是一種型別的結構[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。 其成員儲存對話方塊物件的特性。 在建構之後`CFindReplaceDialog`物件時，您可以使用`m_fr`修改 對話方塊中的各種值。  
  
 如需這個結構的詳細資訊，請參閱**FINDREPLACE**結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。  
  
##  <a name="a-namematchcasea--cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog::MatchCase  
 呼叫此函式可判斷使用者是否想要完全符合尋找字串的大小寫。  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果使用者想要尋找完全符合大小寫的搜尋字串中，搜尋字串的項目否則為 0。  
  
##  <a name="a-namematchwholeworda--cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord  
 呼叫此函式可判斷使用者是否想要比對整個的文字。  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果使用者想要比對整個單字的搜尋字串。否則為 0。  
  
##  <a name="a-namereplacealla--cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog::ReplaceAll  
 呼叫此函式可判斷使用者是否想要被取代字串的所有項目。  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用者已要求，會取代所有相符的取代字串的字串; 如果為非零否則為 0。  
  
##  <a name="a-namereplacecurrenta--cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent  
 呼叫此函式可判斷使用者是否想要取代目前的文字。  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果使用者已要求目前所選的字串會取代在取代字串中。否則為 0。  
  
##  <a name="a-namesearchdowna--cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog::SearchDown  
 呼叫此函式可判斷使用者是否要繼續向下的方向搜尋。  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果使用者想要向下的方向，繼續進行搜尋，非零值。0，如果使用者想要向上繼續搜尋。  
  
## <a name="see-also"></a>另請參閱  
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)  

