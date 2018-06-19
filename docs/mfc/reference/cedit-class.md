---
title: CEdit 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
dev_langs:
- C++
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fba91f4c16c5b356b1e7a11e35380a15eb98eb1
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463075"
---
# <a name="cedit-class"></a>CEdit Class
提供 Windows 編輯控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CEdit : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CEdit::CEdit](#cedit)|建構`CEdit`控制項物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CEdit::CanUndo](#canundo)|決定是否可以復原的編輯控制項作業。|  
|[CEdit::CharFromPos](#charfrompos)|擷取最接近指定位置的字元的行和字元索引。|  
|[CEdit::Clear](#clear)|（清除） 刪除目前選取範圍 （如果有的話） 在編輯控制項。|  
|[CEdit::Copy](#copy)|複製目前選取範圍 （如果有的話） 中編輯控制項到剪貼簿**CF_TEXT**格式。|  
|[CEdit::Create](#create)|建立 Windows 編輯控制項，並將它附加至`CEdit`物件。|  
|[CEdit::Cut](#cut)|刪除 （剪下） 目前的選取範圍 （如果有的話） 在編輯控制，並將刪除的文字複製到剪貼簿**CF_TEXT**格式。|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重設 （清除） 復原旗標的編輯控制項。|  
|[CEdit::FmtLines](#fmtlines)|設定包含軟體的換行字元的開啟或關閉多行編輯控制項中。|  
|[CEdit::GetCueBanner](#getcuebanner)|擷取的文字顯示為文字的提示或提示，在編輯控制項的控制項是空的而且沒有焦點時。|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|決定最上層的可見行編輯控制項中。|  
|[CEdit::GetHandle](#gethandle)|擷取目前的多行編輯控制項的配置的記憶體的控制代碼。|  
|[CEdit::GetHighlight](#gethighlight)|取得的開始和結束的字元會在目前的編輯控制項中反白顯示的文字範圍的索引。|  
|[CEdit::GetLimitText](#getlimittext)|取得這個文字的最大數量`CEdit`可以包含。|  
|[CEdit::GetLine](#getline)|擷取編輯控制項中文字行。|  
|[CEdit::GetLineCount](#getlinecount)|擷取多行編輯控制項中的行數。|  
|[CEdit::GetMargins](#getmargins)|取得這個左、 右邊界`CEdit`。|  
|[CEdit::GetModify](#getmodify)|判斷是否已經修改編輯控制項的內容。|  
|[CEdit::GetPasswordChar](#getpasswordchar)|擷取使用者輸入文字時，編輯控制項中顯示的密碼字元。|  
|[CEdit::GetRect](#getrect)|取得編輯控制項的格式設定的矩形。|  
|[CEdit::GetSel](#getsel)|取得編輯控制項中目前的選取範圍的第一個和最後一個字元位置。|  
|[CEdit::HideBalloonTip](#hideballoontip)|隱藏任何目前的編輯控制項相關聯的汽球提示。|  
|[CEdit::LimitText](#limittext)|限制使用者可以在編輯控制項中輸入文字的長度。|  
|[CEdit::LineFromChar](#linefromchar)|擷取包含指定之字元索引的那一行的行號。|  
|[CEdit::LineIndex](#lineindex)|擷取字元的索引中的多行編輯控制項的線條。|  
|[CEdit::LineLength](#linelength)|擷取編輯控制項中的資料行的長度。|  
|[CEdit::LineScroll](#linescroll)|捲動的多行編輯控制項的文字。|  
|[CEdit::Paste](#paste)|從剪貼簿資料插入編輯控制項，在目前游標位置。 資料會插入剪貼簿包含資料時，才**CF_TEXT**格式。|  
|[CEdit::PosFromChar](#posfromchar)|擷取指定之字元索引左上角的座標。|  
|[CEdit::ReplaceSel](#replacesel)|取代指定的文字編輯控制項中的目前選取範圍。|  
|[CEdit::SetCueBanner](#setcuebanner)|設定會顯示為文字的提示或提示，此控制項是空的而且沒有焦點時的編輯控制項中的文字。|  
|[CEdit::SetHandle](#sethandle)|將控制代碼設定將多行編輯控制項所使用的本機記憶體。|  
|[CEdit::SetHighlight](#sethighlight)|反白顯示的文字會顯示在目前範圍的編輯控制項。|  
|[CEdit::SetLimitText](#setlimittext)|設定此文字的最大數量`CEdit`可以包含。|  
|[CEdit::SetMargins](#setmargins)|設定這個左、 右邊界`CEdit`。|  
|[CEdit::SetModify](#setmodify)|設定或清除編輯控制項的修改旗標。|  
|[CEdit::SetPasswordChar](#setpasswordchar)|設定或移除使用者輸入文字時，編輯控制項中顯示的密碼字元。|  
|[CEdit::SetReadOnly](#setreadonly)|設定編輯控制項的唯讀狀態。|  
|[CEdit::SetRect](#setrect)|設定格式化多行編輯控制項的矩形，並更新控制項。|  
|[CEdit::SetRectNP](#setrectnp)|設定格式化多行編輯控制項的矩形，而不重繪控制項視窗。|  
|[CEdit::SetSel](#setsel)|在編輯控制項中選取字元的範圍。|  
|[CEdit::SetTabStops](#settabstops)|設定定位停駐點在多行編輯控制項。|  
|[CEdit::ShowBalloonTip](#showballoontip)|顯示目前的編輯控制項相關聯的汽球提示。|  
|[CEdit::Undo](#undo)|反轉上一個編輯控制項作業。|  
  
## <a name="remarks"></a>備註  
 編輯控制項是使用者可以在其中輸入文字的矩形的子視窗。  
  
 從對話方塊範本，或是直接在您的程式碼中，您可以建立編輯控制項。 在這兩種情況下，第一次呼叫建構函式`CEdit`建構`CEdit`物件，然後呼叫[建立](#create)成員函式來建立 Windows 編輯控制項，並將其附加至`CEdit`物件。  
  
 建構可以是單一步驟中的處理序類別，衍生自`CEdit`。 寫入的建構函式在衍生的類別並呼叫**建立**從建構函式內。  
  
 `CEdit` 繼承重要的功能，從`CWnd`。 若要設定和擷取從文字`CEdit`物件，請使用`CWnd`成員函式[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext)，編輯的整個內容所控制的 set 或 get，即使它是多行控制項。 多行控制項中的文字行分隔 '\r\n' 字元序列。 此外，如果多行編輯控制項，取得並設定控制項的文字的一部分，藉由呼叫`CEdit`成員函式[GetLine](#getline)， [SetSel](#setsel)， [GetSel](#getsel)，和[ReplaceSel](#replacesel)。  
  
 如果您想要處理 Windows 通知訊息編輯控制項傳送至其父代 (通常的類別衍生自`CDialog`)，將訊息對應項目和訊息處理常式成員函式加入至每個訊息的父類別。  
  
 每個訊息對應項目有下列形式：  
  
  **ON_**_通知_**(** _識別碼_**，** _memberFxn_ **)**
  
 其中`id`指定傳送通知的編輯控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 在父系的函式原型如下所示：  
  
 **afx_msg** void memberFxn **（);**  
  
 以下是一份潛在的訊息對應項目和描述，它們就會傳送到父代的案例：  
  
- **ON_EN_CHANGE**使用者採取的動作，可能已更改編輯控制項中的文字。 不同於**EN_UPDATE** ，這項通知訊息會傳送通知訊息在 Windows 更新顯示。  
  
- **ON_EN_ERRSPACE**編輯控制項無法配置足夠的記憶體，以符合特定的要求。  
  
- **ON_EN_HSCROLL**使用者編輯控制項的水平捲軸。 更新螢幕之前，會通知父視窗。  
  
- **ON_EN_KILLFOCUS**編輯控制項失去輸入的焦點。  
  
- **ON_EN_MAXTEXT**目前的插入動作已超過指定的編輯控制項的字元數，並已經截斷。 編輯控制項沒有時，也傳送**ES_AUTOHSCROLL**樣式和要插入的字元數會超過編輯控制項的寬度。 編輯控制項沒有時，也傳送**ES_AUTOVSCROLL**樣式和所產生的文字插入行的總數超過編輯控制項的高度。  
  
- **ON_EN_SETFOCUS**傳送編輯控制項收到輸入的焦點時。  
  
- **ON_EN_UPDATE**即將顯示變更的文字編輯控制項。 傳送控制項已格式化文字後，但它螢幕文字，以便可以變更視窗大小，如有必要。  
  
- **ON_EN_VSCROLL**使用者編輯控制項的垂直捲軸。 更新螢幕之前，會通知父視窗。  
  
 如果您建立`CEdit`內對話方塊中，物件`CEdit`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CEdit`從對話方塊資源使用對話方塊編輯器中，物件`CEdit`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CEdit`物件內的視窗中，您可能也需要終結。 如果您建立`CEdit`物件在堆疊上，會自動終結。 如果您建立`CEdit`使用堆積上的物件**新**函式，您必須呼叫**刪除**當使用者終止 Windows 終結該物件上的編輯控制項。 如果您配置任何記憶體`CEdit`物件，請覆寫`CEdit`解構函式來處置的配置。  
  
 若要修改編輯控制項中的某些樣式 (例如**ES_READONLY**) 必須將特定的訊息傳送至控制項而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 請參閱[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)Windows SDK 中。  
  
 如需有關`CEdit`，請參閱：  
  
- [控制項](../../mfc/controls-mfc.md)  
  
-   知識庫文章 Q259949： 資訊： SetCaretPos() 是不適當與 CEdit 或 CRichEditCtrl 控制項  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="canundo"></a>  CEdit::CanUndo  
 呼叫此函式來判斷是否可以復原上次的編輯作業。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果上次的編輯作業復原呼叫非零，**復原**成員函式，則為 0，如果無法復原。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::Undo](#undo)。  
  
##  <a name="cedit"></a>  CEdit::CEdit  
 建構 `CEdit` 物件。  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>備註  
 使用[建立](#create)來建構 Windows 編輯控制項。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="charfrompos"></a>  CEdit::CharFromPos  
 呼叫此函式可擷取的以零為起始的行與最接近指定的點，在這個字元的字元索引`CEdit`控制項  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 工作區中此點的座標`CEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 中的字元索引的低序位**WORD**，高順序的行索引和**WORD**。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="clear"></a>  CEdit::Clear  
 呼叫此函式來刪除 （清除） 目前的選取範圍 （如果有的話） 中編輯控制項。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 所執行的刪除**清除**可以藉由呼叫復原[復原](#undo)成員函式。  
  
 若要刪除目前選取範圍，並已刪除的內容放入剪貼簿，請呼叫[剪下](#cut)成員函式。  
  
 如需詳細資訊，請參閱[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="copy"></a>  CEdit::Copy  
 呼叫此函式以下列方式複製目前的選取範圍 （如果有的話） 到剪貼簿中的編輯控制項中**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="create"></a>  CEdit::Create  
 建立 Windows 編輯控制項，並將它附加至`CEdit`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定編輯控制項的樣式。 套用的任何組合[編輯樣式](styles-used-by-mfc.md#edit-styles)至控制項。  
  
 `rect`  
 指定編輯控制項的大小和位置。 可以是`CRect`物件或`RECT`結構。  
  
 `pParentWnd`  
 指定編輯控制項的父視窗 (通常`CDialog`)。 它不得為**NULL**。  
  
 `nID`  
 指定編輯控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 您建構`CEdit`兩個步驟中的物件。 首先，呼叫`CEdit`建構函式，然後再呼叫**建立**，建立 Windows 編輯控制項，並將它附加至`CEdit`物件。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635)， [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634)， [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619)，和[WM_GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626)之編輯控制項的訊息。  
  
 這些訊息會由預設的[OnNcCreate](cwnd-class.md#onnccreate)， [OnNcCalcSize](cwnd-class.md#onnccalcsize)， [OnCreate](cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成員函式在`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CEdit`、 將訊息對應新增到新的類別，並覆寫上述的訊息處理常式成員函式。 覆寫`OnCreate`，例如，執行所需的初始化新的類別。  
  
 套用下列[視窗樣式](styles-used-by-mfc.md#window-styles)編輯控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**群組控制項  
  
- **WS_TABSTOP** tab 鍵順序中包含編輯控制項  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="cut"></a>  CEdit::Cut  
 呼叫此函式來刪除 （剪下） 編輯控制項中目前的選取範圍 （如果有的話） 和刪除的文字複製到剪貼簿**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>備註  
 所執行的刪除**剪下**可以藉由呼叫復原[復原](#undo)成員函式。  
  
 若要刪除目前選取範圍不需將刪除的文字放到剪貼簿，請呼叫[清除](#clear)成員函式。  
  
 如需詳細資訊，請參閱[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer  
 編輯控制項的復原旗標呼叫此函式可重設 （清除）。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>備註  
 編輯控制項現在會無法復原最後一項作業。 編輯控制項中的作業可以復原時，會設定復原旗標。  
  
 復原旗標，則會自動清除每當[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[sethandle，然後](#sethandle)`CWnd`成員函式的呼叫。  
  
 如需詳細資訊，請參閱[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="fmtlines"></a>  CEdit::FmtLines  
 呼叫此函式可設定多行編輯控制項中包含虛換行字元的 on 或 off。  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>參數  
 *bAddEOL*  
 指定是否要插入軟換行字元。 值為**TRUE**插入下列字元:; 值為**FALSE**會將它們移除。  
  
### <a name="return-value"></a>傳回值  
 如果有任何非零，就會發生格式化;否則便是 0。  
  
### <a name="remarks"></a>備註  
 軟分行符號包含兩個歸位字元和換行字元插入已中斷，因為自動換行尾。 硬碟分行符號是由一個歸位字元和換行字元所組成。 結尾硬碟分行符號的線不會受到`FmtLines`。  
  
 如果，只會回應 Windows`CEdit`物件是多行編輯控制項。  
  
 `FmtLines` 只會影響所傳回的緩衝區[GetHandle](#gethandle)和所傳回的文字[WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627)。 它的文字編輯控制項中顯示沒有任何影響。  
  
 如需詳細資訊，請參閱[EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="getcuebanner"></a>  CEdit::GetCueBanner  
 擷取會顯示為文字的提示或提示，當控制項是空的編輯控制項中的文字。  
  
```  
BOOL GetCueBanner(
    LPWSTR lpszText,  
    int cchText) const;  
  
CString GetCueBanner() const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lpszText`  
 包含提示文字的字串指標。  
  
 [輸入] `cchText`  
 可以接受的字元數。 這個數目包括終止`NULL`字元。  
  
### <a name="return-value"></a>傳回值  
 第一個多載，如`true`方法是否成功，否則`false`。  
  
 第二個多載， [CString](../../atl-mfc-shared/using-cstring.md) ，其中包含提示文字，如果方法成功則為空字串 ("")。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572) Windows SDK 中所述的訊息。 如需詳細資訊，請參閱[Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695)巨集。  
  
##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine  
 呼叫此函式來判斷最上層的可見行編輯控制項中。  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>傳回值  
 最上層的可見行以零為起始的索引。 對單行編輯控制項，則傳回值為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="gethandle"></a>  CEdit::GetHandle  
 呼叫此函式可擷取多行編輯控制項的目前配置的記憶體的控制代碼。  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 識別編輯控制項內容的緩衝區本機記憶體控制代碼。 如果發生錯誤，例如傳送訊息至單行編輯控制項，則傳回值為 0。  
  
### <a name="remarks"></a>備註  
 控制代碼的本機記憶體控制代碼，而且可由任一**本機**Windows 記憶體函式採用本機記憶體處理做為參數。  
  
 **GetHandle**處理只能由多行編輯控制項。  
  
 呼叫**GetHandle**只有當對話方塊中所建立的對話方塊中的多行編輯控制項**DS_LOCALEDIT**樣式旗標集。 如果**DS_LOCALEDIT**樣式未設定，您仍可以使用非零的傳回值，但不是能使用傳回的值。  
  
> [!NOTE]
> **GetHandle**不適用於 Windows 95/98。 如果您呼叫**GetHandle**在 Windows 95/98，它會傳回**NULL**。 **GetHandle**運作 Windows NT 3.51 及更新版本底下所述。  
  
 如需詳細資訊，請參閱[EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="gethighlight"></a>  CEdit::GetHighlight  
 會在目前的編輯控制項中反白顯示的文字範圍中取得第一個和最後一個字元的索引。  
  
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
 這個方法會傳送[EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578) Windows SDK 中所述的訊息。  
  
##  <a name="getlimittext"></a>  CEdit::GetLimitText  
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
  
 如需詳細資訊，請參閱[EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="getline"></a>  CEdit::GetLine  
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
 指定的行號，來擷取多行編輯控制項。 行號是以零為起始。值為 0 指定的第一行。 這個參數已忽略由單行編輯控制項。  
  
 `lpszBuffer`  
 指向接收複本之線條的緩衝區。 第一個單字的緩衝區必須指定最大可以複製到緩衝區的字元數。  
  
 `nMaxLength`  
 指定可複製至緩衝區的位元組數目上限。 `GetLine` 將此值放在第一個單字的`lpszBuffer`產生 windows 呼叫之前。  
  
### <a name="return-value"></a>傳回值  
 實際複製的位元組數。 傳回值為 0，如果所指定的行號`nIndex`大於編輯控制項中的行數。  
  
### <a name="remarks"></a>備註  
 所複製的行不包含 null 結束字元。  
  
 如需詳細資訊，請參閱[EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::GetLineCount](#getlinecount)。  
  
##  <a name="getlinecount"></a>  CEdit::GetLineCount  
 呼叫此函式可擷取多行編輯控制項中的行數。  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含多行中的行號的整數的編輯控制項。 如果沒有文字輸入至編輯控制項，則傳回值為 1。  
  
### <a name="remarks"></a>備註  
 `GetLineCount` 只會處理多行編輯控制項。  
  
 如需詳細資訊，請參閱[EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="getmargins"></a>  CEdit::GetMargins  
 呼叫此成員函式可擷取此編輯控制項的左右邊界。  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在低序位左邊界的寬度**WORD**以及高序位的右邊界的寬度**WORD**。  
  
### <a name="remarks"></a>備註  
 邊界會以像素為單位測量。  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="getmodify"></a>  CEdit::GetModify  
 呼叫此函式可判斷是否已經修改編輯控制項的內容。  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果編輯控制項內容已經遭到修改。0，如果它們有仍維持不變。  
  
### <a name="remarks"></a>備註  
 Windows 會維護內部的旗標，指出是否已變更編輯控制項的內容。 當編輯控制項第一次建立也可能會藉由呼叫清除時，清除此旗標[SetModify](#setmodify)成員函式。  
  
 如需詳細資訊，請參閱[EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar  
 呼叫此函式可擷取使用者輸入文字時，會顯示在編輯控制項中的密碼字元。  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定要顯示而不是使用者輸入的字元的字元。 傳回值是`NULL`有密碼的字元。  
  
### <a name="remarks"></a>備註  
 如果您建立與編輯控制項**ES_PASSWORD**樣式，為支援控制項的 DLL 會決定預設的密碼字元。 資訊清單或[InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697)方法決定哪些 DLL 支援編輯控制項。 如果 user32.dll 支援編輯控制項的預設密碼字元是星號 ('* '，U + 002A)。 如果 comctl32.dll 版本 6 支援編輯控制項的預設字元是黑色圓形 （'●'，U + 25CF）。 如需有關哪些 DLL 和版本支援的通用控制項，請參閱[殼層和通用控制項版本](http://msdn.microsoft.com/library/windows/desktop/bb776779)。  
  
 這個方法會傳送[EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="getrect"></a>  CEdit::GetRect  
 呼叫此函式可取得格式化編輯控制項的矩形。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`接收格式化矩形的結構。  
  
### <a name="remarks"></a>備註  
 格式化的矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。  
  
 格式化多行編輯控制項的矩形可以修改[SetRect](#setrect)和[SetRectNP](#setrectnp)成員函式。  
  
 如需詳細資訊，請參閱[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::LimitText](#limittext)。  
  
##  <a name="getsel"></a>  CEdit::GetSel  
 呼叫此函式可取得開始和結束的字元位置的目前選取範圍 （如果有的話） 中編輯控制項，使用傳回值或參數。  
  
```  
DWORD GetSel() const;  
  
void GetSel(
    int& nStartChar,  
    int& nEndChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartChar`  
 整數，會在目前的選取範圍中收到第一個字元的位置參考。  
  
 `nEndChar`  
 整數，將會收到的未選取的第一個字元，超過目前的選取範圍結尾的位置參考。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本`DWORD`傳回值，這個值包含高序位文字中的選取範圍結尾之後的低序位字組中的開始位置和未選取的第一個字元的位置。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip  
 隱藏任何目前的編輯控制項相關聯的汽球提示。  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此函式會將[EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604) Windows SDK 中所述的訊息。  
  
##  <a name="limittext"></a>  CEdit::LimitText  
 呼叫此函式來限制使用者可能會在編輯控制項中輸入文字的長度。  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>參數  
 `nChars`  
 指定使用者可以輸入文字的長度 （以位元組為單位）。 這個參數是 0，如果文字長度會設定為**UINT_MAX**位元組。 這是預設行為。  
  
### <a name="remarks"></a>備註  
 變更文字限制會限制只會使用者可以輸入的文字。 它不會影響任何文字中已有編輯控制項，也不會影響複製到編輯控制項的文字的長度[SetWindowText](cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項比指定的呼叫中放`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者以新文字取代現有的文字，除非刪除目前選取範圍會導致要低於文字限制的文字。  
  
> [!NOTE]
>  在 Win32 中 （Windows NT 和 Windows 95/98） [SetLimitText](#setlimittext)取代此函式。  
  
 如需詳細資訊，請參閱[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="linefromchar"></a>  CEdit::LineFromChar  
 呼叫此函式可擷取包含指定之字元索引的那一行的行號。  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含編輯控制項的文字中所需的字元的以零為起始的索引值，或包含-1。 如果`nIndex`為-1，它會指定目前這一行，也就是包含插入號的那一行。  
  
### <a name="return-value"></a>傳回值  
 包含所指定的字元索引的那一行的以零為起始的行號`nIndex`。 如果`nIndex`為-1，會傳回包含選取範圍的第一個字元的行號。 如果沒有選取範圍，則會傳回目前的行號。  
  
### <a name="remarks"></a>備註  
 字元索引會從編輯控制項的開頭的字元數。  
  
 此成員函式只供多行編輯控制項。  
  
 如需詳細資訊，請參閱[EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="lineindex"></a>  CEdit::LineIndex  
 呼叫此函式可擷取的一行內的多行編輯控制項的字元索引。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nLine`  
 包含編輯控制項的文字行的索引值，或包含-1。 如果`nLine`為-1，它會指定目前這一行，也就是包含插入號的那一行。  
  
### <a name="return-value"></a>傳回值  
 在指定的行的字元索引`nLine`則為-1 指定的行號大於編輯控制項中的行數。  
  
### <a name="remarks"></a>備註  
 字元索引是指定行編輯控制項的開頭字元數。  
  
 多行編輯控制項只會處理此成員函式。  
  
 如需詳細資訊，請參閱[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="linelength"></a>  CEdit::LineLength  
 擷取編輯控制項中的資料行的長度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nLine`  
 其長度是要擷取的行中的字元以零為起始的索引。 預設值為 -1。  
  
### <a name="return-value"></a>傳回值  
 對單行編輯控制項，則傳回值是長度在`TCHAR`s，編輯控制項中的文字。  
  
 對於多行編輯控制項的傳回值位於長度`TCHAR`s，行所指定的`nLine`參數。 如[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]文字，長度為行中的位元組數目; Unicode 文字的長度為行中的字元數。 長度不包含行尾的歸位字元。  
  
 如果`nLine`參數大於控制項中的字元數、 傳回值為零。  
  
 如果`nLine`參數為-1，傳回的值是包含選取的字元的行中未選取的字元數。 例如，如果從一條從下一行的結尾的第八個字元的第四個字元，延伸選取範圍，則傳回值為 10。 也就是三個字元的第一行和七個在下一次。  
  
 如需有關`TCHAR`類型，請參閱`TCHAR`資料表中的資料列[Windows 資料類型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>備註  
 這個方法會受到[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::LineIndex](#lineindex)。  
  
##  <a name="linescroll"></a>  CEdit::LineScroll  
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
 指定要水平捲動字元位置的數目。 會忽略此值，如果編輯控制項已經**ES_RIGHT**或**ES_CENTER**樣式。  
  
### <a name="remarks"></a>備註  
 多行編輯控制項只會處理此成員函式。  
  
 編輯控制項無法以垂直方式捲動過去的文字編輯控制項中的最後一行。 如果目前的行加上所指定的線條數目`nLines`超過的編輯控制項中的總行數，值會進行調整，以便編輯控制項的最後一行捲動至編輯控制項視窗的頂端。  
  
 `LineScroll` 可以用於水平捲動，過去的任何一行的最後一個字元。  
  
 如需詳細資訊，請參閱[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="paste"></a>  CEdit::Paste  
 呼叫此函式可將資料從剪貼簿`CEdit`的插入點。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>備註  
 資料會插入剪貼簿包含資料時，才**CF_TEXT**格式。  
  
 如需詳細資訊，請參閱[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="posfromchar"></a>  CEdit::PosFromChar  
 呼叫此函式可取得指定的字元在這個位置 （左上角）`CEdit`物件。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 指定的字元以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 所指定的字元左上角的座標`nChar`。  
  
### <a name="remarks"></a>備註  
 藉由以零為起始的索引值會指定字元。 如果`nChar`大於最後一個字元在這個索引`CEdit`物件，傳回的值在此指定剛好超過最後一個字元的字元位置的座標`CEdit`物件。  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::LineFromChar](#linefromchar)。  
  
##  <a name="replacesel"></a>  CEdit::ReplaceSel  
 呼叫此函式，以取代所指定的文字編輯控制項中的目前選取範圍`lpszNewText`。  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `lpszNewText`  
 指向以 null 終止的字串，包含取代文字。  
  
 `bCanUndo`  
 指定此函式可以復原，請設定此參數的值**TRUE** 。 預設值是**FALSE**。  
  
### <a name="remarks"></a>備註  
 取代只包含編輯控制項中文字的一部分。 如果您要取代的所有文字，請使用[CWnd::SetWindowText](cwnd-class.md#setwindowtext)成員函式。  
  
 如果沒有目前選取範圍，取代文字會插入在目前游標位置。  
  
 如需詳細資訊，請參閱[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::LineIndex](#lineindex)。  
  
##  <a name="setcuebanner"></a>  CEdit::SetCueBanner  
 設定會顯示為文字提示中，或提示、 在 編輯控制當控制項是空的文字。  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszText`  
 包含要編輯控制項中顯示提示的字串指標。  
  
 [輸入] `fDrawWhenFocused`  
 如果`false`，當使用者在編輯控制項中按一下，並會將焦點置於控制項不會繪製提示橫幅。  
  
 如果`true`，即使當焦點在控制項繪製提示橫幅。 當使用者開始在控制項中輸入時，就會消失提示橫幅。  
  
 預設值是 `false`。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果方法成功。否則`false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639) Windows SDK 中所述的訊息。 如需詳細資訊，請參閱[Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703)巨集。  
  
### <a name="example"></a>範例  
 下列範例會示範[CEdit::SetCueBanner](#setcuebanner)方法。  
  
 [!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="sethandle"></a>  CEdit::SetHandle  
 呼叫此函式可將多行編輯控制項所使用的本機記憶體設定的控制代碼。  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>參數  
 *hBuffer*  
 包含本機記憶體的控制代碼。 這個控制代碼必須都由先前呼叫[LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) Windows 函式使用**LMEM_MOVEABLE**旗標。 假設記憶體是包含以 null 結束的字串。 如果這不是大小寫，第一個位元組的配置的記憶體應該設定為 0。  
  
### <a name="remarks"></a>備註  
 編輯控制項接著會使用這個緩衝區來儲存目前顯示的文字，而不是它自己的緩衝區配置。  
  
 多行編輯控制項只會處理此成員函式。  
  
 應用程式設定新的記憶體處理之前，應該使用[GetHandle](#gethandle)成員函式取得目前的記憶體緩衝區的控制代碼，並釋放該記憶體使用**LocalFree** Windows 函式。  
  
 `SetHandle` 清除恢復緩衝區 ( [CanUndo](#canundo)成員函式會傳回 0) 和內部修改旗標 ( [GetModify](#getmodify)成員函式會傳回 0)。 編輯控制項視窗會重新繪製。  
  
 您可以使用此多行編輯控制項中的成員函式在對話方塊中，只有當您建立與對話方塊**DS_LOCALEDIT**樣式旗標集。  
  
> [!NOTE]
> **GetHandle**不適用於 Windows 95/98。 如果您呼叫**GetHandle**在 Windows 95/98，它會傳回**NULL**。 **GetHandle**運作 Windows NT 3.51 及更新版本底下所述。  
  
 如需詳細資訊，請參閱[EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641)， [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)，和[LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="sethighlight"></a>  CEdit::SetHighlight  
 反白顯示的文字會顯示在目前範圍的編輯控制項。  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `ichStart`|要反白顯示的文字範圍的第一個字元的以零為起始的索引。|  
|[輸入] `ichEnd`|要反白顯示的文字範圍的最後一個字元的以零為起始的索引。|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643) Windows SDK 中所述的訊息。  
  
##  <a name="setlimittext"></a>  CEdit::SetLimitText  
 呼叫此成員函式設定這個文字限制`CEdit`物件。  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `nMax`  
 新文字的限制，以字元為單位。  
  
### <a name="remarks"></a>備註  
 文字限制為文字，以字元為單位，編輯控制項可接受的最大數量。  
  
 變更文字限制會限制只會使用者可以輸入的文字。 它不會影響任何文字中已有編輯控制項，也不會影響複製到編輯控制項的文字的長度[SetWindowText](cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項比指定的呼叫中放`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者以新文字取代現有的文字，除非刪除目前選取範圍會導致要低於文字限制的文字。  
  
 這個函式取代[LimitText](#limittext)在 Win32 中。  
  
 如需詳細資訊，請參閱[EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="setmargins"></a>  CEdit::SetMargins  
 呼叫此方法以設定此編輯控制項的左右邊界。  
  
```  
void SetMargins(
    UINT nLeft,  
    UINT nRight);
```  
  
### <a name="parameters"></a>參數  
 *nLeft*  
 新的左邊界，單位為像素寬度。  
  
 *nRight*  
 新的右邊界，單位為像素寬度。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  此成員函式是 Windows 95 及 Windows NT 4.0 的開頭。  
  
 如需詳細資訊，請參閱[EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="setmodify"></a>  CEdit::SetModify  
 呼叫此函式可設定或清除編輯控制項的已修改旗標。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 值為**TRUE**指出已經修改文字，而值為**FALSE**指出它是未修改。 根據預設，會設定已修改的旗標。  
  
### <a name="remarks"></a>備註  
 修改過的旗標會指出已經修改編輯控制項中的文字。 它會自動設定每次使用者變更文字。 其值可能會擷取與[GetModify](#getmodify)成員函式。  
  
 如需詳細資訊，請參閱[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::GetModify](#getmodify)。  
  
##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar  
 呼叫此函式可設定或移除當使用者輸入的文字編輯控制項中顯示的密碼字元。  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>參數  
 *ch*  
 指定要顯示使用者輸入的字元取代的字元。 如果*ch*為 0，則會顯示使用者輸入的實際字元。  
  
### <a name="remarks"></a>備註  
 設定密碼字元時，該字元所顯示的每個字元的使用者類型。  
  
 此成員函式有不會影響多行編輯控制項。  
  
 當`SetPasswordChar`呼叫成員函式時，`CEdit`將會重新繪製所有可見的字元，使用指定的字元*ch*。  
  
 如果編輯控制項以建立[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)樣式，預設的密碼字元設為星號 ( **\***)。 如果已移除，此樣式`SetPasswordChar`呼叫*ch*設為 0。  
  
 如需詳細資訊，請參閱[EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="setreadonly"></a>  CEdit::SetReadOnly  
 呼叫此函式可將編輯控制項的唯讀狀態。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bReadOnly`  
 指定是否要設定或移除編輯控制項的唯讀狀態。 值為**TRUE**將狀態設定為唯讀，而值**FALSE**設定為讀取/寫入狀態。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果作業成功，則為 0 如果發生錯誤，就會發生。  
  
### <a name="remarks"></a>備註  
 可以測試所發現的目前設定[ES_READONLY](styles-used-by-mfc.md#edit-styles)的傳回值中的旗標[CWnd::GetStyle](cwnd-class.md#getstyle)。  
  
 如需詳細資訊，請參閱[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="setrect"></a>  CEdit::SetRect  
 呼叫此函式可設定使用指定的座標之矩形的維度。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件，指定新格式化矩形的維度。  
  
### <a name="remarks"></a>備註  
 多行編輯控制項只會處理這個成員。  
  
 使用`SetRect`若要設定的格式設定矩形的多行編輯控制項。 格式化的矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。 編輯控制項最初建立時，格式化矩形是編輯控制項視窗的工作區相同。 使用`SetRect`成員函式，大於或小於編輯控制項視窗的應用程式可以進行格式化的矩形。  
  
 如果編輯控制項有沒有捲軸，文字會裁剪，不會經過包裝，如果超過視窗進行格式化的矩形。 如果編輯控制項包含框線，格式化的矩形的框線大小減少。 如果您調整所傳回的矩形`GetRect`成員函式，您必須移除框線的大小，才能傳遞至矩形`SetRect`。  
  
 當`SetRect`稱為，編輯控制項的文字也重新格式化並重新顯示。  
  
 如需詳細資訊，請參閱[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="setrectnp"></a>  CEdit::SetRectNP  
 呼叫此函式可設定多行編輯控制項的格式設定的矩形。  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件，指定矩形的新維度。  
  
### <a name="remarks"></a>備註  
 格式化的矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。  
  
 `SetRectNP` 等同於`SetRect`成員函式不同之處在於不重新繪製編輯控制項視窗。  
  
 編輯控制項最初建立時，格式化矩形是編輯控制項視窗的工作區相同。 藉由呼叫`SetRectNP`成員函式，大於或小於編輯控制項視窗的應用程式可以進行格式化的矩形。  
  
 如果編輯控制項有沒有捲軸，文字會裁剪，不會經過包裝，如果超過視窗進行格式化的矩形。  
  
 多行編輯控制項只會處理這個成員。  
  
 如需詳細資訊，請參閱[EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::SetRect](#setrect)。  
  
##  <a name="setsel"></a>  CEdit::SetSel  
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
 指定低序位字組中的開始位置和高序位文字的結束位置。 如果低序位字組是 0，高序位文字是-1，會選取編輯控制項中的所有文字。 如果低序位字組為-1，則會移除任何目前的選取範圍。  
  
 *bNoScroll*  
 指出插入號是否應該捲動到檢視。 如果**FALSE**，插入號捲動到檢視。 如果**TRUE**，插入號不會捲動到檢視。  
  
 `nStartChar`  
 指定的開始位置。 如果`nStartChar`為 0 和`nEndChar`為-1，所有選取的文字編輯控制項中。 如果`nStartChar`為-1，會移除任何目前的選取範圍。  
  
 `nEndChar`  
 指定的結束位置。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEdit::GetSel](#getsel)。  
  
##  <a name="settabstops"></a>  CEdit::SetTabStops  
 呼叫此函式中的多行編輯控制項設定定位停駐點。  
  
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
 指定包含在定位停駐點數目`rgTabStops`。 這個數字必須大於 1。  
  
 `rgTabStops`  
 對話方塊單位中，停止指向指定的索引標籤的不帶正負號整數的陣列。 對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一，而 1 個垂直對話方塊單位等於目前對話方塊基底高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 **GetDialogBaseUnits** Windows 函式會傳回目前對話方塊基本單位像素為單位。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已設定索引標籤。否則便是 0。  
  
### <a name="remarks"></a>備註  
 文字複製到多行編輯控制項，在文字中的任何 tab 字元會產生到下一個定位停駐點的空間。  
  
 若要設定 32 個對話方塊單位的預設大小的定位停駐點，呼叫此成員函式的無參數的版本。 若要設定定位停駐點的大小以外 32，呼叫與版本`cxEachStop`參數。 若要設定定位停駐點大小的陣列，使用具有兩個參數的版本。  
  
 多行編輯控制項只會處理此成員函式。  
  
 `SetTabStops` 不會自動重新繪製 [編輯] 視窗。 如果您變更已在編輯控制項中文字的定位停駐點時，呼叫[CWnd::InvalidateRect](cwnd-class.md#invalidaterect)重繪 [編輯] 視窗。  
  
 如需詳細資訊，請參閱[EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663)和[GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CEditView::SetTabStops](ceditview-class.md#settabstops)。  
  
##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip  
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
|[輸入] `pEditBalloonTip`|指標[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)結構描述之氣球提示。|  
|[輸入] `lpszTitle`|包含的汽球提示標題的 Unicode 字串指標。|  
|[輸入] `lpszText`|包含氣球提示文字的 Unicode 字串指標。|  
|[輸入] `ttiIcon`|`INT`指定圖示與氣球提示的型別。 預設值是 `TTI_NONE`。 如需詳細資訊，請參閱`ttiIcon`隸屬[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)結構。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此函式會將[EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668) Windows SDK 中所述的訊息。 如需詳細資訊，請參閱[Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707)巨集。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_cedit`，也就是用來存取目前的編輯控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例顯示氣球提示的編輯控制項。 [CEdit::ShowBalloonTip](#showballoontip)方法指定的標題和氣球提示文字。  
  
 [!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="undo"></a>  CEdit::Undo  
 呼叫此函式可復原上次的編輯控制項作業。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>傳回值  
 對於單行編輯控制項一律是為非零，傳回的值。 對於多行編輯控制項中，如果復原作業成功，則為非零的傳回值是 0 則復原作業會失敗。  
  
### <a name="remarks"></a>備註  
 復原作業，也可以復原。 比方說，您可以還原已刪除的文字的第一個呼叫**復原**。 只要沒有任何中介的編輯作業，您可以移除一次與第二個呼叫的文字**復原**。  
  
 如需詳細資訊，請參閱[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
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
