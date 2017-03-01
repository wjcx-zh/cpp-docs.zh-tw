---
title: "CEdit 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEdit
dev_langs:
- C++
helpviewer_keywords:
- separators, in multiline edit controls
- text editors
- controls [MFC], edit
- text editors, CEdit class
- edit controls, classes
- multiline edit control
- CEdit class
- line separators in multiline edit controls
- edit controls
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
caps.latest.revision: 22
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
ms.openlocfilehash: 9c782e77b1fdb9026ee030238413955ba4d537e9
ms.lasthandoff: 02/24/2017

---
# <a name="cedit-class"></a>CEdit Class
提供 Windows 編輯控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CEdit : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CEdit::CEdit](#cedit)|建構`CEdit`控制項物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CEdit::CanUndo](#canundo)|判斷是否可復原的編輯控制項作業。|  
|[CEdit::CharFromPos](#charfrompos)|擷取最接近指定位置的字元的行與字元索引。|  
|[CEdit::Clear](#clear)|（清除） 刪除目前選取範圍 （如果有的話） 中編輯控制。|  
|[CEdit::Copy](#copy)|複製目前的選取範圍 （如果有的話） 中編輯控制項到剪貼簿**CF_TEXT**格式。|  
|[CEdit::Create](#create)|建立 Windows 編輯控制項並將它附加`CEdit`物件。|  
|[CEdit::Cut](#cut)|刪除 （剪下） 目前的選取範圍 （如果有的話） 中編輯控制，並將已刪除的文字複製到剪貼簿**CF_TEXT**格式。|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重設 （清除） 復原旗標的編輯控制項。|  
|[CEdit::FmtLines](#fmtlines)|設定開啟或關閉軟體換行字元的多行編輯控制項中。|  
|[CEdit::GetCueBanner](#getcuebanner)|擷取文字提示和秘訣，當控制項是空的並不具有焦點的編輯控制項中顯示的文字。|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|決定最上層的可見行編輯控制項中。|  
|[CEdit::GetHandle](#gethandle)|擷取多行編輯控制項的目前配置的記憶體的控制代碼。|  
|[CEdit::GetHighlight](#gethighlight)|取得開始和結束目前的編輯控制項中反白顯示的文字範圍中的字元的索引。|  
|[CEdit::GetLimitText](#getlimittext)|取得這個文字的最大數量`CEdit`可以包含。|  
|[CEdit::GetLine](#getline)|擷取編輯控制項中的一行文字。|  
|[CEdit::GetLineCount](#getlinecount)|擷取多行編輯控制項中的行數。|  
|[CEdit::GetMargins](#getmargins)|取得這個左、 右邊界`CEdit`。|  
|[CEdit::GetModify](#getmodify)|判斷是否已修改編輯控制項的內容。|  
|[CEdit::GetPasswordChar](#getpasswordchar)|擷取使用者輸入文字時，編輯控制項中顯示的密碼字元。|  
|[CEdit::GetRect](#getrect)|取得格式編輯控制項的矩形。|  
|[CEdit::GetSel](#getsel)|取得編輯控制項中目前的選取範圍的第一個和最後一個字元位置。|  
|[CEdit::HideBalloonTip](#hideballoontip)|隱藏任何目前的編輯控制項相關聯的汽球提示。|  
|[CEdit::LimitText](#limittext)|限制使用者可以編輯控制項中輸入文字的長度。|  
|[CEdit::LineFromChar](#linefromchar)|擷取包含指定之的字元索引的那一行的行號。|  
|[CEdit::LineIndex](#lineindex)|擷取多行編輯控制項中一行的字元索引。|  
|[CEdit::LineLength](#linelength)|擷取編輯控制項中的資料行的長度。|  
|[CEdit::LineScroll](#linescroll)|捲動多行編輯控制項的文字。|  
|[CEdit::Paste](#paste)|從剪貼簿資料插入目前游標位置的編輯控制項。 資料會插入剪貼簿中包含的資料時，才**CF_TEXT**格式。|  
|[CEdit::PosFromChar](#posfromchar)|擷取指定之的字元索引左上角的座標。|  
|[CEdit::ReplaceSel](#replacesel)|取代指定的文字編輯控制項中的目前選取範圍。|  
|[CEdit::SetCueBanner](#setcuebanner)|設定文字提示和秘訣，當控制項是空的並不具有焦點的編輯控制項中顯示的文字。|  
|[CEdit::SetHandle](#sethandle)|將控制代碼設定將多行編輯控制項所使用的本機記憶體。|  
|[CEdit::SetHighlight](#sethighlight)|反白顯示的文字會顯示在目前範圍的編輯控制項。|  
|[CEdit::SetLimitText](#setlimittext)|設定文字的最大數量`CEdit`可以包含。|  
|[CEdit::SetMargins](#setmargins)|設定這個左、 右邊界`CEdit`。|  
|[CEdit::SetModify](#setmodify)|設定或清除編輯控制項的修改旗標。|  
|[CEdit::SetPasswordChar](#setpasswordchar)|設定或移除當使用者進入文字編輯控制項中顯示的密碼字元。|  
|[CEdit::SetReadOnly](#setreadonly)|設定編輯控制項的唯讀狀態。|  
|[CEdit::SetRect](#setrect)|設定多行編輯控制項的格式化矩形，並更新控制項。|  
|[CEdit::SetRectNP](#setrectnp)|設定多行編輯控制項的格式化矩形，而不重繪控制項視窗。|  
|[CEdit::SetSel](#setsel)|Edit 控制項中選取字元的範圍。|  
|[CEdit::SetTabStops](#settabstops)|設定定位停駐點，在多行編輯控制項。|  
|[CEdit::ShowBalloonTip](#showballoontip)|顯示目前的編輯控制項相關聯的汽球提示。|  
|[CEdit::Undo](#undo)|會反轉最後一個編輯控制項作業。|  
  
## <a name="remarks"></a>備註  
 編輯控制項是使用者可以在其中輸入文字的矩形的子視窗。  
  
 從對話方塊範本，或是直接在您的程式碼中，您可以建立編輯控制項。 在這兩種情況下，第一次呼叫建構函式`CEdit`建構`CEdit`物件，然後呼叫[建立](#create)成員函式來建立 Windows 編輯控制項，並將其附加至`CEdit`物件。  
  
 建構可從衍生類別中的一蹴`CEdit`。 寫入的建構函式在衍生的類別並呼叫**建立**從建構函式內。  
  
 `CEdit`繼承重要的功能，從`CWnd`。 設定及擷取文字從`CEdit`物件，請使用`CWnd`成員函式[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext)，設定或取得編輯控制項的整個內容，即使它是多行的控制項。 在多行控制項中的文字行隔開 '\r\n' 字元序列。 此外，如果多行編輯控制項，取得並設定控制項的文字的一部分，藉由呼叫`CEdit`成員函式[GetLine](#getline)， [SetSel](#setsel)， [GetSel](#getsel)，和[ReplaceSel](#replacesel)。  
  
 如果您想要處理 Windows 通知訊息傳送至其父代編輯控制項 (通常是一個類別衍生自`CDialog`)，將訊息對應項目和訊息處理常式成員函式加入至每個訊息的父類別。  
  
 每個訊息對應項目都會使用下列格式︰  
  
 **ON_**通知**(** *識別碼、 memberFxn***)**  
  
 其中`id`指定傳送通知的編輯控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 父函式原型如下所示︰  
  
 **afx_msg** void memberFxn **（);**  
  
 下列是可能的訊息對應項目和描述的情況下以它們會傳送至父清單︰  
  
- **ON_EN_CHANGE**使用者採取的動作，可能有變更的編輯控制項中的文字。 不同於**EN_UPDATE**通知訊息時，這會傳送通知訊息後 Windows 更新顯示。  
  
- **ON_EN_ERRSPACE**編輯控制項無法配置足夠的記憶體，以符合特定要求。  
  
- **ON_EN_HSCROLL**使用者按一下 編輯控制項的水平捲軸。 螢幕更新之前，父視窗會收到通知。  
  
- **ON_EN_KILLFOCUS**編輯控制項失去輸入的焦點。  
  
- **ON_EN_MAXTEXT**目前插入已超過指定的編輯控制項的字元數，且已遭截斷。 沒有編輯控制項時，也傳送**ES_AUTOHSCROLL**樣式和要插入的字元數會超過編輯控制項的寬度。 沒有編輯控制項時，也傳送**ES_AUTOVSCROLL**樣式和文字插入所產生的總行數會超過編輯控制項的高度。  
  
- **ON_EN_SETFOCUS**傳送編輯控制項收到輸入的焦點時。  
  
- **ON_EN_UPDATE**即將顯示變更的文字編輯控制項。 控制項已格式化文字之後，但它螢幕文字以確保可以變更視窗大小，如有必要之前傳送。  
  
- **ON_EN_VSCROLL**使用者按一下 編輯控制項的垂直捲軸。 螢幕更新之前，父視窗會收到通知。  
  
 如果您建立`CEdit`內對話方塊中，物件`CEdit`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CEdit`對話方塊資源使用對話方塊編輯器中，從物件`CEdit`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CEdit`視窗中，您可能也需要它終結物件。 如果您建立`CEdit`物件在堆疊上，它會自動終結。 如果您建立`CEdit`使用堆積上的物件**新**函式，您必須呼叫**刪除**使用者終止 Windows 時終結該物件上編輯控制項。 如果您配置任何記憶體`CEdit`物件，覆寫`CEdit`解構函式配置的處置。  
  
 若要修改特定樣式的編輯控制項中 (例如**ES_READONLY**) 必須將特定的訊息傳送至控制項而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 請參閱[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關`CEdit`，請參閱︰  
  
- [控制項](../../mfc/controls-mfc.md)  
  
-   知識庫文件 Q259949︰ 資訊︰ SetCaretPos() 是不適當與 CEdit 或 CRichEditCtrl 控制項  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecanundoa--ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo  
 呼叫此函式來判斷是否可以復原上次的編輯作業。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果呼叫復原上次的編輯作業為非零**復原**成員函式，則為 0，如果無法復原。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::Undo](#undo)。  
  
##  <a name="a-namecedita--ceditcedit"></a><a name="cedit"></a>CEdit::CEdit  
 建構 `CEdit` 物件。  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>備註  
 使用[建立](#create)來建構 Windows 編輯控制項。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&1;](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="a-namecharfromposa--ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharFromPos  
 呼叫此函式可擷取的以零為起始的行與最接近指定點中字元的字元索引`CEdit`控制項  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 這個工作區中的點座標`CEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 中的字元索引的低序位**WORD**，以及高順序的列索引**WORD**。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&3;](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="a-namecleara--ceditclear"></a><a name="clear"></a>CEdit::Clear  
 呼叫此函式來刪除 (clear) 目前的選取範圍 （如果有的話） 中編輯控制項。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 刪除由**清除**可以藉由呼叫復原[復原](#undo)成員函式。  
  
 若要刪除目前選取範圍，並將已刪除的內容放到剪貼簿，呼叫[剪下](#cut)成員函式。  
  
 如需詳細資訊，請參閱[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&4;](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="a-namecopya--ceditcopy"></a><a name="copy"></a>CEdit::Copy  
 呼叫此函式以下列方式複製目前的選取範圍 （如果有的話） 中編輯控制項以剪貼簿中**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&5;](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="a-namecreatea--ceditcreate"></a><a name="create"></a>CEdit::Create  
 建立 Windows 編輯控制項並將它附加`CEdit`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定編輯控制項的樣式。 套用的任何結合[編輯樣式](edit-styles.md)至控制項。  
  
 `rect`  
 指定編輯控制項的大小和位置。 可以是`CRect`物件或`RECT`結構。  
  
 `pParentWnd`  
 指定編輯控制項的父視窗 (通常是`CDialog`)。 它不得為**NULL**。  
  
 `nID`  
 指定編輯控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CEdit`兩個步驟中的物件。 首先，呼叫`CEdit`建構函式，然後呼叫**建立**，其建立 Windows 編輯控制項，並將它附加`CEdit`物件。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635)， [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634)， [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619)，和[WM_GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626)編輯控制項的訊息。  
  
 根據預設，處理這些訊息[OnNcCreate](cwnd-class.md#onnccreate)， [OnNcCalcSize](cwnd-class.md#onnccalcsize)， [OnCreate](cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成員函式中`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CEdit`、 將訊息對應新增至新的類別，並覆寫上述的訊息處理常式成員函式。 覆寫`OnCreate`，例如，執行所需的初始化新的類別。  
  
 適用於下列[視窗樣式](window-styles.md)來編輯控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**控制項群組  
  
- **WS_TABSTOP**包含編輯控制項的定位順序  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&2;](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="a-namecuta--ceditcut"></a><a name="cut"></a>CEdit::Cut  
 呼叫此函式來刪除 （剪下） 編輯控制項中目前的選取範圍 （如果有的話），並將已刪除的文字複製到剪貼簿中**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>備註  
 刪除由**剪下**可以藉由呼叫復原[復原](#undo)成員函式。  
  
 若要刪除目前選取範圍，而不將已刪除的文字放入剪貼簿，呼叫[清除](#clear)成員函式。  
  
 如需詳細資訊，請參閱[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&6;](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="a-nameemptyundobuffera--ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer  
 編輯控制項的復原旗標呼叫此函式來重設 （清除）。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>備註  
 編輯控制項現在無法復原最後一個作業。 只要編輯控制項中的作業可以復原設定復原旗標。  
  
 復原旗標會自動清除每當[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle) `CWnd`成員函式的呼叫。  
  
 如需詳細資訊，請參閱[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&7;](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="a-namefmtlinesa--ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines  
 呼叫此函式可開啟或關閉設定軟換行字元包含在多行編輯控制項中。  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>參數  
 *bAddEOL*  
 指定是否要插入虛換行字元。 值為**TRUE**插入下列字元:; 值為**FALSE**會將它們移除。  
  
### <a name="return-value"></a>傳回值  
 如果有任何非零格式就會發生。否則為 0。  
  
### <a name="remarks"></a>備註  
 非強制換行符號是由兩個歸位字元和已中斷，因為自動換行的結尾插入換行字元所組成。 硬碟換行符號是由一個歸位字元和換行字元所組成。 硬碟分行符號以結尾的行不會受到`FmtLines`。  
  
 如果只會回應 Windows`CEdit`物件都是多行編輯控制項。  
  
 `FmtLines`只會影響所傳回的緩衝區[GetHandle](#gethandle)所傳回的文字和[WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627)。 它在螢幕上顯示的文字編輯控制項中沒有任何影響。  
  
 如需詳細資訊，請參閱[EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&8;](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="a-namegetcuebannera--ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner  
 擷取文字提示和秘訣，當控制項是空白的編輯控制項中顯示的文字。  
  
```  
BOOL GetCueBanner(
    LPWSTR lpszText,  
    int cchText) const;  
  
CString GetCueBanner() const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lpszText`  
 包含提示文字的字串指標。  
  
 [in] `cchText`  
 可以接受的字元數。 這個數目包括終止`NULL`字元。  
  
### <a name="return-value"></a>傳回值  
 第一個多載，如`true`如果方法成功，否則為`false`。  
  
 適用於第二個多載， [CString](../../atl-mfc-shared/using-cstring.md) ，其中包含提示文字，如果方法成功，否則為空字串 ("")。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需詳細資訊，請參閱[Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695)巨集。  
  
##  <a name="a-namegetfirstvisiblelinea--ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine  
 呼叫此函式可判斷最上層的可見行編輯控制項中。  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>傳回值  
 最上層的可見行以零為起始的索引。 單行編輯控制項，則傳回值為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&9;](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="a-namegethandlea--ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle  
 呼叫此函式可擷取多行編輯控制項的目前配置的記憶體的處理常式。  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 識別編輯控制項的內容的緩衝區本機記憶體控制代碼。 如果發生錯誤，例如將訊息傳送至單一行編輯控制項，則傳回值為 0。  
  
### <a name="remarks"></a>備註  
 控制代碼是本機記憶體的控制代碼和任何可能使用**本機**Windows 記憶體函式會在本機記憶體處理做為參數。  
  
 **GetHandle**只會由多行編輯控制項。  
  
 呼叫**GetHandle**才以建立對話方塊中的對話方塊中的多行編輯控制項的**DS_LOCALEDIT**樣式旗標。 如果**DS_LOCALEDIT**樣式未設定，您仍然可以取得非零的傳回值，但不是能使用傳回的值。  
  
> [!NOTE]
> **GetHandle**不適用於 Windows 95/98。 如果您呼叫**GetHandle**在 Windows 95/98，它會傳回**NULL**。 **GetHandle**運作，將會說明在 Windows NT 3.51 及更新版本。  
  
 如需詳細資訊，請參閱[EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&10;](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="a-namegethighlighta--ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight  
 會反白顯示目前的編輯控制項中的文字範圍中取得第一個和最後一個字元的索引。  
  
```  
BOOL GetHighlight(
    int* pichStart,   
    int* pichEnd) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `pichStart`|會反白顯示的文字範圍的第一個字元的以零為起始的索引。|  
|[輸出] `pichEnd`|會反白顯示的文字範圍的最後一個字元的以零為起始的索引。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetlimittexta--ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText  
 呼叫此成員函式，以取得此文字限制`CEdit`物件。  
  
```  
UINT GetLimitText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前文字的限制，以位元組為單位，這個`CEdit`物件。  
  
### <a name="remarks"></a>備註  
 文字限制為文字，以位元組為單位，編輯控制項可接受的最大數量。  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&11;](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="a-namegetlinea--ceditgetline"></a><a name="getline"></a>CEdit::GetLine  
 呼叫此函式可擷取編輯控制項中的一行文字，並將它放入`lpszBuffer`。  
  
```  
int GetLine(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
int GetLine(
    int nIndex,  
    LPTSTR lpszBuffer,  
    int nMaxLength) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定的行號，以擷取從多行編輯控制項。 行號是以零起始。0 值指定的第一行。 這個參數已忽略由單一行編輯控制項。  
  
 `lpszBuffer`  
 收到一份列的緩衝區的指標。 緩衝區的第一個單字必須指定最大可以複製到緩衝區的字元數。  
  
 `nMaxLength`  
 指定可以複製至緩衝區的位元組數目上限。 `GetLine`將此值放入的第一個字`lpszBuffer`產生呼叫 windows 之前。  
  
### <a name="return-value"></a>傳回值  
 實際複製的位元組數。 傳回值為 0，如果所指定的行號`nIndex`大於編輯控制項中的行數。  
  
### <a name="remarks"></a>備註  
 所複製的行不包含 null 結束字元。  
  
 如需詳細資訊，請參閱[EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::GetLineCount](#getlinecount)。  
  
##  <a name="a-namegetlinecounta--ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount  
 呼叫此函式可擷取的多行編輯控制項中的行數。  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含多行中的行號的整數的編輯控制項。 如果在編輯控制項中不輸入任何文字，則傳回值為 1。  
  
### <a name="remarks"></a>備註  
 `GetLineCount`只會處理多行編輯控制項。  
  
 如需詳細資訊，請參閱[EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&12;](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="a-namegetmarginsa--ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins  
 呼叫此成員函式擷取此編輯控制項的左、 右邊界。  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在低序位左邊界的寬度**WORD**高序位的右邊界的寬度和**WORD**。  
  
### <a name="remarks"></a>備註  
 邊界被測量單位為像素。  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="a-namegetmodifya--ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify  
 呼叫此函式可判斷是否已經修改編輯控制項的內容。  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果在編輯控制項內容已經被修改。0，表示它們保持不變。  
  
### <a name="remarks"></a>備註  
 Windows 會維護內部的旗標，指出是否已變更編輯控制項的內容。 當編輯控制項第一次建立時可能也會清除呼叫時，清除此旗標[SetModify](#setmodify)成員函式。  
  
 如需詳細資訊，請參閱[EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&13;](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="a-namegetpasswordchara--ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar  
 呼叫此函式可擷取使用者輸入文字時，會顯示在編輯控制項中的密碼字元。  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定要顯示而不是使用者輸入的字元的字元。 傳回值是`NULL`有沒有密碼字元。  
  
### <a name="remarks"></a>備註  
 如果您建立與編輯控制項**ES_PASSWORD**樣式，支援控制 DLL 決定預設的密碼字元。 資訊清單或[InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697)方法決定哪些 DLL 支援編輯控制項。 預設密碼字元 user32.dll 支援編輯控制項，如果是星號 ('* '，U +&002;A)。 如果 comctl32.dll 版本 6 支援編輯控制項的預設字元是黑色圓形 （'●'，U + 25CF）。 如需有關哪些 DLL 和版本支援的通用控制項，請參閱[殼層和通用控制項版本](http://msdn.microsoft.com/library/windows/desktop/bb776779)。  
  
 這個方法會傳送[EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&14;](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="a-namegetrecta--ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect  
 呼叫此函式可取得編輯控制項的格式設定的矩形。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`接收格式化矩形的結構。  
  
### <a name="remarks"></a>備註  
 格式化矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。  
  
 您可以修改格式化多行編輯控制項的矩形[SetRect](#setrect)和[SetRectNP](#setrectnp)成員函式。  
  
 如需詳細資訊，請參閱[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::LimitText](#limittext)。  
  
##  <a name="a-namegetsela--ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel  
 呼叫此函式可取得的起始和結束目前的選取範圍 （如果有的話） 中編輯控制項，使用傳回值或參數的字元位置。  
  
```  
DWORD GetSel() const;  
  
void GetSel(
    int& nStartChar,  
    int& nEndChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartChar`  
 整數，會在目前的選取範圍收到第一個字元的位置參考。  
  
 `nEndChar`  
 整數，將會收到第一個未選取目前的選取範圍的結尾字元的位置參考。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本`DWORD`傳回值，這個值，其中包含高序位文字中的選取範圍的結尾之後的低序位字組中的開始位置和未選取第一個字元的位置。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&15;](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="a-namehideballoontipa--cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip  
 隱藏任何目前的編輯控制項相關聯的汽球提示。  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此函式會將[EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namelimittexta--ceditlimittext"></a><a name="limittext"></a>CEdit::LimitText  
 呼叫此函式來限制使用者可以編輯控制項中輸入文字的長度。  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>參數  
 `nChars`  
 指定使用者可以輸入之文字的長度 （以位元組為單位）。 這個參數是 0，如果文字長度會設定為**UINT_MAX**位元組。 這是預設行為。  
  
### <a name="remarks"></a>備註  
 變更文字的限制會限制只顯示使用者可以輸入的文字。 它有任何文字不會影響已經在編輯控制項中，也不會影響編輯控制項所複製的文字長度[SetWindowText](cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項的呼叫中指定以外置於`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者使用新的文字來取代現有的文字，除非刪除目前選取範圍會造成要低於文字限制的文字。  
  
> [!NOTE]
>  在 Win32 中 （Windows NT 和 Windows 95/98） [SetLimitText](#setlimittext)會取代此函式。  
  
 如需詳細資訊，請參閱[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&17;](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="a-namelinefromchara--ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineFromChar  
 呼叫此函式可擷取包含指定之的字元索引的那一行的行號。  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含編輯控制項的文字中所需的字元以零為起始的索引值，或包含-1。 如果`nIndex`為 –&1;，它會指定目前的行，也就是包含游標的那一行。  
  
### <a name="return-value"></a>傳回值  
 包含所指定的字元索引的行的以零為起始的行號`nIndex`。 如果`nIndex`為 –&1;，會傳回包含選取範圍的第一個字元的行號。 如果沒有選取範圍，則會傳回目前的行號。  
  
### <a name="remarks"></a>備註  
 字元索引是從編輯控制項的開頭的字元數。  
  
 多行編輯控制項只會使用這個成員函式。  
  
 如需詳細資訊，請參閱[EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&18;](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="a-namelineindexa--ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex  
 呼叫此函式可擷取多行編輯控制項中一行的字元索引。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nLine`  
 包含要在編輯控制項的文字行的索引值，或包含-1。 如果`nLine`為 –&1;，它會指定目前的行，也就是包含游標的那一行。  
  
### <a name="return-value"></a>傳回值  
 在指定的行的字元索引`nLine`則為 –&1;，如果指定的行號大於編輯控制項中的行數。  
  
### <a name="remarks"></a>備註  
 字元索引是指定行編輯控制項的開頭字元數。  
  
 多行編輯控制項只會處理此成員函式。  
  
 如需詳細資訊，請參閱[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&19;](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="a-namelinelengtha--ceditlinelength"></a><a name="linelength"></a>CEdit::LineLength  
 擷取編輯控制項中的資料行的長度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nLine`  
 其長度是要擷取的一行中的字元以零為起始的索引。 預設值為 -1。  
  
### <a name="return-value"></a>傳回值  
 單行編輯控制項的傳回值是長度，在`TCHAR`s，編輯控制項中的文字。  
  
 對於多行編輯控制項，則傳回值是長度，在`TCHAR`s，行所指定的`nLine`參數。 如[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]文字，長度為行中的位元組數目; Unicode 文字，長度為行中的字元數。 長度不包含行尾的歸位字元。  
  
 如果`nLine`參數為多個控制項中的字元數，則傳回值是零。  
  
 如果`nLine`參數為 –&1;，傳回的值是包含選取之的字元的程式行中未選取的字元數。 例如，如果從一條從下一行結尾的第八個字元的第四個字元，延伸選取範圍，則傳回值為 10。 也就是三個字元的第一行和七個在下一次。  
  
 如需詳細資訊`TCHAR`輸入資訊，請參閱`TCHAR`資料表中的資料列[Windows 資料類型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>備註  
 這個方法支援[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::LineIndex](#lineindex)。  
  
##  <a name="a-namelinescrolla--ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll  
 呼叫此函式可捲動的多行編輯控制項的文字。  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>參數  
 `nLines`  
 指定要垂直捲動行的數。  
  
 `nChars`  
 指定要水平捲動字元位置的數目。 如果具有編輯控制項，會忽略此值**ES_RIGHT**或**ES_CENTER**樣式。  
  
### <a name="remarks"></a>備註  
 多行編輯控制項只會處理此成員函式。  
  
 編輯控制項不會以垂直方式捲動，過去的文字編輯控制項中的最後一行。 如果目前的行加上所指定的行數`nLines`超過編輯控制項中的總行數，值會調整，使編輯控制項的最後一行捲動到 編輯控制項視窗的頂端。  
  
 `LineScroll`可以用於水平捲動過去的任何一行的最後一個字元。  
  
 如需詳細資訊，請參閱[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="a-namepastea--ceditpaste"></a><a name="paste"></a>CEdit::Paste  
 呼叫此函式可將資料從剪貼簿`CEdit`的插入點。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>備註  
 資料會插入剪貼簿中包含的資料時，才**CF_TEXT**格式。  
  
 如需詳細資訊，請參閱[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&20;](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="a-nameposfromchara--ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PosFromChar  
 呼叫此函式可取得指定的字元在這個位置 （左上角），`CEdit`物件。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 指定的字元以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 所指定之字元的左上角的座標`nChar`。  
  
### <a name="remarks"></a>備註  
 藉由以零為起始的索引值會指定字元。 如果`nChar`大於最後一個字元在這個索引`CEdit`物件，傳回的值在此指定正好超過最後一個字元的字元位置的座標`CEdit`物件。  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::LineFromChar](#linefromchar)。  
  
##  <a name="a-namereplacesela--ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel  
 呼叫此函式，以取代所指定的文字編輯控制項中目前的選取`lpszNewText`。  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `lpszNewText`  
 指向以 null 結束的字串，包含取代文字。  
  
 `bCanUndo`  
 若要指定可以復原此函式，來設定此參數，以值**TRUE** 。 預設值是**FALSE**。  
  
### <a name="remarks"></a>備註  
 取代只包含編輯控制項中文字的一部分。 如果您要取代的所有文字，請使用[CWnd::SetWindowText](cwnd-class.md#setwindowtext)成員函式。  
  
 如果沒有目前選取範圍，取代文字會插入目前的游標位置。  
  
 如需詳細資訊，請參閱[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::LineIndex](#lineindex)。  
  
##  <a name="a-namesetcuebannera--ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner  
 設定顯示為文字提示中，或秘訣，在編輯，來控制當控制項是空的文字。  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszText`  
 包含要編輯控制項中顯示提示的字串指標。  
  
 [in] `fDrawWhenFocused`  
 如果`false`，當使用者在編輯控制項中按一下，並提供控制項焦點不會繪製提示橫幅。  
  
 如果`true`，即使當焦點在控制項繪製提示橫幅。 當使用者開始輸入控制項中時，就會消失提示橫幅。  
  
 預設值是 `false`。  
  
### <a name="return-value"></a>傳回值  
 `true`如果方法成功。否則`false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需詳細資訊，請參閱[Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703)巨集。  
  
### <a name="example"></a>範例  
 下列範例會示範[CEdit::SetCueBanner](#setcuebanner)方法。  
  
 [!code-cpp[NVC_MFC_CEdit_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="a-namesethandlea--ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle  
 呼叫此函式可將多行編輯控制項所使用的本機記憶體設定的控制代碼。  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>參數  
 *hBuffer*  
 包含本機記憶體的控制代碼。 這個控制代碼必須都由先前呼叫[LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)函式所使用的 Windows **LMEM_MOVEABLE**旗標。 記憶體會假設包含以 null 結束的字串。 如果情況並非如此，配置的記憶體中的第一個位元組應該設定為 0。  
  
### <a name="remarks"></a>備註  
 編輯控制項接著會使用這個緩衝區來儲存目前顯示的文字，而不是它自己的緩衝區配置。  
  
 多行編輯控制項只會處理此成員函式。  
  
 應用程式設定新的記憶體處理之前，應該使用[GetHandle](#gethandle)成員函式，取得目前的記憶體緩衝區的控制代碼，並釋放該記憶體使用**LocalFree** Windows 函式。  
  
 `SetHandle`清除恢復緩衝區 ( [CanUndo](#canundo)成員函式則會傳回 0) 和內部修改旗標 ( [GetModify](#getmodify)成員函式則會傳回 0)。 編輯控制項的視窗會重新繪製。  
  
 您可以使用此多行編輯控制項中的成員函式在對話方塊中，只有當您建立對話方塊**DS_LOCALEDIT**樣式旗標。  
  
> [!NOTE]
> **GetHandle**不適用於 Windows 95/98。 如果您呼叫**GetHandle**在 Windows 95/98，它會傳回**NULL**。 **GetHandle**運作，將會說明在 Windows NT 3.51 及更新版本。  
  
 如需詳細資訊，請參閱[EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641)， [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)，和[LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&22;](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="a-namesethighlighta--ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight  
 反白顯示的文字會顯示在目前範圍的編輯控制項。  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `ichStart`|反白顯示的文字範圍的第一個字元的以零為起始的索引。|  
|[in] `ichEnd`|反白顯示的文字範圍的最後一個字元的以零為起始的索引。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetlimittexta--ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText  
 呼叫此成員函式，以便將此文字限制`CEdit`物件。  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `nMax`  
 新文字的限制，以字元為單位。  
  
### <a name="remarks"></a>備註  
 文字限制為文字，請在編輯控制項可接受的字元數目上限。  
  
 變更文字的限制會限制只顯示使用者可以輸入的文字。 它有任何文字不會影響已經在編輯控制項中，也不會影響編輯控制項所複製的文字長度[SetWindowText](cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項的呼叫中指定以外置於`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者使用新的文字來取代現有的文字，除非刪除目前選取範圍會造成要低於文字限制的文字。  
  
 這個函式取代[LimitText](#limittext)在 Win32 中。  
  
 如需詳細資訊，請參閱[EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="a-namesetmarginsa--ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins  
 呼叫這個方法來設定此編輯控制項的左、 右邊界。  
  
```  
void SetMargins(
    UINT nLeft,  
    UINT nRight);
```  
  
### <a name="parameters"></a>參數  
 *nLeft*  
 新的左邊界，單位為像素的寬度。  
  
 *nRight*  
 新的右邊界，單位為像素的寬度。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="a-namesetmodifya--ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify  
 呼叫此函式可設定或清除編輯控制項的已修改旗標。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 值為**TRUE**表示文字已修改，而值為**FALSE**指出它是未經修改。 根據預設，會設定已修改的旗標。  
  
### <a name="remarks"></a>備註  
 修改過的旗標會指出已修改的文字編輯控制項中。 它會自動設定每次使用者變更文字。 其值可能會擷取與[GetModify](#getmodify)成員函式。  
  
 如需詳細資訊，請參閱[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::GetModify](#getmodify)。  
  
##  <a name="a-namesetpasswordchara--ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar  
 呼叫此函式可設定或移除當使用者輸入的文字編輯控制項中顯示的密碼字元。  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>參數  
 *ch*  
 指定要顯示使用者輸入的字元取代的字元。 如果*ch*是 0，則會顯示使用者輸入的實際字元。  
  
### <a name="remarks"></a>備註  
 設定密碼字元時，該字元會顯示每個字元的使用者類型。  
  
 此成員函式具有不會影響多行編輯控制項。  
  
 當`SetPasswordChar`呼叫成員函式時，`CEdit`會重繪其所有可見的字元，使用指定的字元*ch*。  
  
 如果編輯控制項以建立[ES_PASSWORD](edit-styles.md)樣式，預設的密碼字元會設定為星號 ( ** \* **)。 如果移除這個樣式`SetPasswordChar`呼叫*ch*設為 0。  
  
 如需詳細資訊，請參閱[EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&16;](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="a-namesetreadonlya--ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly  
 呼叫此函式可設定編輯控制項的唯讀狀態。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bReadOnly`  
 指定是否要設定或移除編輯控制項的唯讀狀態。 值為**TRUE**將狀態設定為唯讀，而值**FALSE**設定為讀取/寫入狀態。  
  
### <a name="return-value"></a>傳回值  
 非零，如果作業成功，則為 0，如果錯誤發生。  
  
### <a name="remarks"></a>備註  
 目前的設定可以找到測試[ES_READONLY](edit-styles.md)中的傳回值的旗標[CWnd::GetStyle](cwnd-class.md#getstyle)。  
  
 如需詳細資訊，請參閱[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&23;](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="a-namesetrecta--ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect  
 呼叫此函式可設定使用指定的座標是矩形的維度。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件，指定新的格式化矩形維度。  
  
### <a name="remarks"></a>備註  
 多行編輯控制項只會處理這個成員。  
  
 使用`SetRect`若要設定格式矩形的多行編輯控制項。 格式化矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。 編輯控制項第一次建立時，格式化矩形是編輯控制項視窗的工作區相同。 使用`SetRect`成員函式，大於或小於編輯控制項視窗應用程式可以進行格式化的矩形。  
  
 如果編輯控制項不有任何捲軸，文字會遭到裁剪，並未包裝，如果超過視窗進行格式化的矩形。 如果編輯控制項包含框線，框線的大小減少格式化的矩形。 如果您調整所傳回的矩形`GetRect`成員函式，您必須移除框線的大小，才能傳遞至矩形`SetRect`。  
  
 當`SetRect`呼叫時，編輯控制項的文字是也重新格式化和重新顯示。  
  
 如需詳細資訊，請參閱[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&24;](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="a-namesetrectnpa--ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP  
 呼叫此函式可設定多行編輯控制項的格式設定的矩形。  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件，指定新的維度的矩形。  
  
### <a name="remarks"></a>備註  
 格式化矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。  
  
 `SetRectNP`等同於`SetRect`成員函式不同之處在於編輯控制項的視窗不會重新繪製。  
  
 編輯控制項第一次建立時，格式化矩形是編輯控制項視窗的工作區相同。 藉由呼叫`SetRectNP`成員函式，大於或小於編輯控制項視窗應用程式可以進行格式化的矩形。  
  
 如果編輯控制項不有任何捲軸，文字會遭到裁剪，並未包裝，如果超過視窗進行格式化的矩形。  
  
 多行編輯控制項只會處理這個成員。  
  
 如需詳細資訊，請參閱[EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::SetRect](#setrect)。  
  
##  <a name="a-namesetsela--ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel  
 呼叫此函式可在編輯控制項中選取的字元範圍。  
  
```  
void SetSel(
    DWORD dwSelection,  
    BOOL bNoScroll = FALSE);

 
void SetSel(
    int nStartChar,  
    int nEndChar,  
    BOOL bNoScroll = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *dwSelection*  
 指定的低序位文字中的開始位置和高序位文字的結束位置。 如果低序位字組為 0，而高序位文字會是 – 1，會選取 編輯控制項中的所有文字。 如果低序位字組為 –&1;，則會移除任何目前的選取範圍。  
  
 *bNoScroll*  
 指出是否應該插入號捲動到檢視。 如果**FALSE**，插入號捲動到檢視。 如果**TRUE**，插入號不會捲動到檢視。  
  
 `nStartChar`  
 指定的開始位置。 如果`nStartChar`為 0 和`nEndChar`為 – 1，所有已選取 編輯控制項中的文字。 如果`nStartChar`為 –&1;，會移除任何目前的選取範圍。  
  
 `nEndChar`  
 指定的結束位置。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEdit::GetSel](#getsel)。  
  
##  <a name="a-namesettabstopsa--ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabStops  
 呼叫此函式可在多行編輯控制項中設定定位停駐點。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>參數  
 `cxEachStop`  
 指定在設定定位停駐點每`cxEachStop`對話方塊單位。  
  
 `nTabStops`  
 指定包含在定位停駐點的數目`rgTabStops`。 這個數字必須大於 1。  
  
 `rgTabStops`  
 對話方塊單位停止指向指定的索引標籤上的不帶正負號整數的陣列。 對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一和 1 個垂直對話方塊單位等於目前對話方塊基底高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 **GetDialogBaseUnits** Windows 函式會傳回目前對話方塊基底單位像素為單位。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已設定索引標籤。否則為 0。  
  
### <a name="remarks"></a>備註  
 文字複製到多行編輯控制項，在文字中的任何索引標籤字元會產生至下一個定位停駐點的空間。  
  
 若要設定 32 個對話方塊單位的預設大小的定位停駐點，呼叫此成員函式的無參數的版本。 若要設定定位停駐點 32 以外的大小，呼叫與版本`cxEachStop`參數。 若要設定定位停駐點大小的陣列，使用具有兩個參數的版本。  
  
 多行編輯控制項只會處理此成員函式。  
  
 `SetTabStops`不會自動重新繪製編輯視窗。 如果您變更已經在編輯控制項中文字的定位停駐點時，呼叫[CWnd::InvalidateRect](cwnd-class.md#invalidaterect)重繪編輯視窗。  
  
 如需詳細資訊，請參閱[EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663)和[GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CEditView::SetTabStops](ceditview-class.md#settabstops)。  
  
##  <a name="a-nameshowballoontipa--ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::ShowBalloonTip  
 顯示目前的編輯控制項相關聯的汽球提示。  
  
```  
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

 
BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,   
    LPCWSTR lpszText,   
    INT ttiIcon = TTI_NONE);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pEditBalloonTip`|指標[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)該結構描述的汽球提示。|  
|[in] `lpszTitle`|包含的汽球提示標題的 Unicode 字串的指標。|  
|[in] `lpszText`|包含汽球提示文字的 Unicode 字串的指標。|  
|[in] `ttiIcon`|`INT`指定汽球提示相關聯的圖示類型。 預設值是 `TTI_NONE`。 如需詳細資訊，請參閱`ttiIcon`成員[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)結構。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此函式會將[EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需詳細資訊，請參閱[Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707)巨集。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_cedit`，也就是用來存取目前的編輯控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CEdit_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會顯示為編輯控制項的汽球提示。 [CEdit::ShowBalloonTip](#showballoontip)方法指定標題和註解方塊的提示文字。  
  
 [!code-cpp[NVC_MFC_CEdit_s&#1;&3;](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="a-nameundoa--ceditundo"></a><a name="undo"></a>CEdit::Undo  
 呼叫此函式可復原上次的編輯控制項作業。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>傳回值  
 對於單一行編輯控制項，傳回的值永遠是零。 對於多行編輯控制項，傳回值為非零，如果復原作業成功，則為 0，如果復原作業失敗。  
  
### <a name="remarks"></a>備註  
 復原作業也會復原。 例如，您可以還原已刪除的文字，與第一次呼叫**復原**。 只要沒有任何中介的編輯作業，您可以移除第二次呼叫一次的文字**復原**。  
  
 如需詳細資訊，請參閱[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit #&25;](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CALCDRIV](../../visual-cpp-samples.md)   
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](cwnd-class.md)   
 [CButton 類別](cbutton-class.md)   
 [CComboBox 類別](ccombobox-class.md)   
 [CListBox 類別](clistbox-class.md)   
 [CScrollBar 類別](cscrollbar-class.md)   
 [CStatic 類別](cstatic-class.md)   
 [CDialog 類別](cdialog-class.md)

