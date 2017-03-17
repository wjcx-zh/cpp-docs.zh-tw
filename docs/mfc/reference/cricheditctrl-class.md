---
title: "CRichEditCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCtrl
- AFXCMN/CRichEditCtrl
- AFXCMN/CRichEditCtrl::CRichEditCtrl
- AFXCMN/CRichEditCtrl::CanPaste
- AFXCMN/CRichEditCtrl::CanRedo
- AFXCMN/CRichEditCtrl::CanUndo
- AFXCMN/CRichEditCtrl::CharFromPos
- AFXCMN/CRichEditCtrl::Clear
- AFXCMN/CRichEditCtrl::Copy
- AFXCMN/CRichEditCtrl::Create
- AFXCMN/CRichEditCtrl::CreateEx
- AFXCMN/CRichEditCtrl::Cut
- AFXCMN/CRichEditCtrl::DisplayBand
- AFXCMN/CRichEditCtrl::EmptyUndoBuffer
- AFXCMN/CRichEditCtrl::FindText
- AFXCMN/CRichEditCtrl::FindWordBreak
- AFXCMN/CRichEditCtrl::FormatRange
- AFXCMN/CRichEditCtrl::GetCharPos
- AFXCMN/CRichEditCtrl::GetDefaultCharFormat
- AFXCMN/CRichEditCtrl::GetEventMask
- AFXCMN/CRichEditCtrl::GetFirstVisibleLine
- AFXCMN/CRichEditCtrl::GetIRichEditOle
- AFXCMN/CRichEditCtrl::GetLimitText
- AFXCMN/CRichEditCtrl::GetLine
- AFXCMN/CRichEditCtrl::GetLineCount
- AFXCMN/CRichEditCtrl::GetModify
- AFXCMN/CRichEditCtrl::GetOptions
- AFXCMN/CRichEditCtrl::GetParaFormat
- AFXCMN/CRichEditCtrl::GetPunctuation
- AFXCMN/CRichEditCtrl::GetRect
- AFXCMN/CRichEditCtrl::GetRedoName
- AFXCMN/CRichEditCtrl::GetSel
- AFXCMN/CRichEditCtrl::GetSelectionCharFormat
- AFXCMN/CRichEditCtrl::GetSelectionType
- AFXCMN/CRichEditCtrl::GetSelText
- AFXCMN/CRichEditCtrl::GetTextLength
- AFXCMN/CRichEditCtrl::GetTextLengthEx
- AFXCMN/CRichEditCtrl::GetTextMode
- AFXCMN/CRichEditCtrl::GetTextRange
- AFXCMN/CRichEditCtrl::GetUndoName
- AFXCMN/CRichEditCtrl::GetWordWrapMode
- AFXCMN/CRichEditCtrl::HideSelection
- AFXCMN/CRichEditCtrl::LimitText
- AFXCMN/CRichEditCtrl::LineFromChar
- AFXCMN/CRichEditCtrl::LineIndex
- AFXCMN/CRichEditCtrl::LineLength
- AFXCMN/CRichEditCtrl::LineScroll
- AFXCMN/CRichEditCtrl::Paste
- AFXCMN/CRichEditCtrl::PasteSpecial
- AFXCMN/CRichEditCtrl::PosFromChar
- AFXCMN/CRichEditCtrl::Redo
- AFXCMN/CRichEditCtrl::ReplaceSel
- AFXCMN/CRichEditCtrl::RequestResize
- AFXCMN/CRichEditCtrl::SetAutoURLDetect
- AFXCMN/CRichEditCtrl::SetBackgroundColor
- AFXCMN/CRichEditCtrl::SetDefaultCharFormat
- AFXCMN/CRichEditCtrl::SetEventMask
- AFXCMN/CRichEditCtrl::SetModify
- AFXCMN/CRichEditCtrl::SetOLECallback
- AFXCMN/CRichEditCtrl::SetOptions
- AFXCMN/CRichEditCtrl::SetParaFormat
- AFXCMN/CRichEditCtrl::SetPunctuation
- AFXCMN/CRichEditCtrl::SetReadOnly
- AFXCMN/CRichEditCtrl::SetRect
- AFXCMN/CRichEditCtrl::SetSel
- AFXCMN/CRichEditCtrl::SetSelectionCharFormat
- AFXCMN/CRichEditCtrl::SetTargetDevice
- AFXCMN/CRichEditCtrl::SetTextMode
- AFXCMN/CRichEditCtrl::SetUndoLimit
- AFXCMN/CRichEditCtrl::SetWordCharFormat
- AFXCMN/CRichEditCtrl::SetWordWrapMode
- AFXCMN/CRichEditCtrl::StopGroupTyping
- AFXCMN/CRichEditCtrl::StreamIn
- AFXCMN/CRichEditCtrl::StreamOut
- AFXCMN/CRichEditCtrl::Undo
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class, common controls
- CRichEditCtrl class
- formatted text [C++]
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
caps.latest.revision: 26
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
ms.openlocfilehash: 77b8dfb6011831f4e4300096a127f70b26bcc603
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditctrl-class"></a>CRichEditCtrl 類別
提供 Windows Rich Edit 控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRichEditCtrl::CRichEditCtrl](#cricheditctrl)|建構 `CRichEditCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRichEditCtrl::CanPaste](#canpaste)|決定是否剪貼簿的內容可以貼到此 rich edit 控制項。|  
|[CRichEditCtrl::CanRedo](#canredo)|判斷是否有任何控制項的重做佇列中的動作。|  
|[CRichEditCtrl::CanUndo](#canundo)|決定是否可復原的編輯作業。|  
|[CRichEditCtrl::CharFromPos](#charfrompos)|擷取最接近指定點的工作區中編輯控制項的字元的相關資訊。|  
|[CRichEditCtrl::Clear](#clear)|清除目前的選取範圍。|  
|[CRichEditCtrl::Copy](#copy)|將目前的選取範圍複製到剪貼簿。|  
|[CRichEditCtrl::Create](#create)|建立 Windows rich edit 控制項，並將它與此相關聯`CRichEditCtrl`物件。|  
|[CRichEditCtrl::CreateEx](#createex)|建立具有指定的 Windows rich edit 控制項，延伸視窗樣式，並關聯這`CRichEditCtrl`物件。|  
|[CRichEditCtrl::Cut](#cut)|剪下目前的選取範圍到剪貼簿。|  
|[CRichEditCtrl::DisplayBand](#displayband)|會顯示內容的這一部分`CRichEditCtrl`物件。|  
|[CRichEditCtrl::EmptyUndoBuffer](#emptyundobuffer)|重設 （清除） 復原旗標，這個`CRichEditCtrl`物件。|  
|[CRichEditCtrl::FindText](#findtext)|在這個文字會找出`CRichEditCtrl`物件。|  
|[CRichEditCtrl::FindWordBreak](#findwordbreak)|尋找下一個斷之前或之後指定的字元位置，或擷取的字元在該位置的相關資訊。|  
|[CRichEditCtrl::FormatRange](#formatrange)|格式化文字的目標輸出裝置的範圍。|  
|[CRichEditCtrl::GetCharPos](#getcharpos)|判斷指定的字元在這個位置`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetDefaultCharFormat](#getdefaultcharformat)|擷取目前的預設字元格式屬性，在此`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetEventMask](#geteventmask)|擷取此事件遮罩`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetFirstVisibleLine](#getfirstvisibleline)|決定在這個最上層的可見行`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetIRichEditOle](#getiricheditole)|擷取的指標`IRichEditOle`這個 rich edit 控制項的介面。|  
|[CRichEditCtrl::GetLimitText](#getlimittext)|取得所需的使用者可以輸入到此文字限制`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetLine](#getline)|擷取這一行文字`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetLineCount](#getlinecount)|擷取中的行數`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetModify](#getmodify)|判斷這個內容`CRichEditCtrl`自從上次儲存之後變更的物件。|  
|[CRichEditCtrl::GetOptions](#getoptions)|擷取 windows rich edit 控制項選項。|  
|[CRichEditCtrl::GetParaFormat](#getparaformat)|擷取段落格式屬性目前的選取範圍，在此`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetPunctuation](#getpunctuation)|擷取目前的標點符號字元的 rich edit 控制項。 這個訊息是作業系統的僅適用於亞洲語言版本。|  
|[CRichEditCtrl::GetRect](#getrect)|這會擷取格式化矩形`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetRedoName](#getredoname)|如果控制項中的任何重做佇列，請擷取下一個動作，型別。|  
|[CRichEditCtrl::GetSel](#getsel)|取得開始和結束位置，這在目前的選取範圍的`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetSelectionCharFormat](#getselectioncharformat)|擷取格式屬性，這在目前的選取範圍中的字元`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetSelectionType](#getselectiontype)|擷取目前的選取範圍，在此內容的型別`CRichEditCtrl`物件。|  
|[CRichEditCtrl::GetSelText](#getseltext)|在此取得目前選取的文字`CRichEditCtrl`物件|  
|[CRichEditCtrl::GetTextLength](#gettextlength)|擷取文字的長度，以字元為單位，在此`CRichEditCtrl`物件。 不包含結束的 null 字元。|  
|[CRichEditCtrl::GetTextLengthEx](#gettextlengthex)|擷取字元或豐富的編輯 檢視中的位元組的數目。 接受旗標來指示判斷 rich edit 控制項中文字的長度的方法清單|  
|[CRichEditCtrl::GetTextMode](#gettextmode)|擷取目前文字模式和復原層級的 rich edit 控制項。|  
|[CRichEditCtrl::GetTextRange](#gettextrange)|擷取指定的文字範圍。|  
|[CRichEditCtrl::GetUndoName](#getundoname)|如果有的話，請擷取下一個復原動作，型別。|  
|[CRichEditCtrl::GetWordWrapMode](#getwordwrapmode)|擷取目前的文字換行及 rich edit 控制項的 word 新選項。 這個訊息是作業系統的僅適用於亞洲語言版本。|  
|[CRichEditCtrl::HideSelection](#hideselection)|顯示或隱藏目前的選取範圍。|  
|[CRichEditCtrl::LimitText](#limittext)|限制使用者可以輸入的文字數量`CRichEditCtrl`物件。|  
|[CRichEditCtrl::LineFromChar](#linefromchar)|判斷哪一行包含指定的字元。|  
|[CRichEditCtrl::LineIndex](#lineindex)|擷取指定行中的字元索引`CRichEditCtrl`物件。|  
|[CRichEditCtrl::LineLength](#linelength)|擷取指定行中的長度`CRichEditCtrl`物件。|  
|[CRichEditCtrl::LineScroll](#linescroll)|將在此文字捲動`CRichEditCtrl`物件。|  
|[CRichEditCtrl::Paste](#paste)|此 rich edit 控制項中插入剪貼簿的內容。|  
|[CRichEditCtrl::PasteSpecial](#pastespecial)|將剪貼簿的內容插入至這個的 rich edit 控制項中指定的資料格式。|  
|[CRichEditCtrl::PosFromChar](#posfromchar)|擷取指定的字元，在編輯控制項中的用戶端區域座標。|  
|[CRichEditCtrl::Redo](#redo)|取消復原上控制項的重做佇列中的下一個動作。|  
|[CRichEditCtrl::ReplaceSel](#replacesel)|取代目前的選取範圍，在此`CRichEditCtrl`含有指定文字的物件。|  
|[CRichEditCtrl::RequestResize](#requestresize)|這會強制`CRichEditCtrl`来傳送要求的調整大小的通知物件。|  
|[CRichEditCtrl::SetAutoURLDetect](#setautourldetect)|指出是否使用 rich edit 控制項中自動 URL 偵測。|  
|[CRichEditCtrl::SetBackgroundColor](#setbackgroundcolor)|在此設定的背景色彩`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetDefaultCharFormat](#setdefaultcharformat)|將目前的預設字元格式屬性，在此`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetEventMask](#seteventmask)|設定這個事件遮罩`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetModify](#setmodify)|設定或清除此修改旗標`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetOLECallback](#setolecallback)|設定`IRichEditOleCallback`這個 rich edit 控制項的 COM 物件。|  
|[CRichEditCtrl::SetOptions](#setoptions)|設定這個選項`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetParaFormat](#setparaformat)|設定段落格式屬性目前的選取範圍，在此`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetPunctuation](#setpunctuation)|設定 rich edit 控制項的標點符號字元。 這個訊息是作業系統的僅適用於亞洲語言版本。|  
|[CRichEditCtrl::SetReadOnly](#setreadonly)|設定唯讀選項，這個`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetRect](#setrect)|設定這個格式化矩形`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetSel](#setsel)|在此設定選取範圍`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetSelectionCharFormat](#setselectioncharformat)|設定格式屬性，這在目前的選取範圍中的字元`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetTargetDevice](#settargetdevice)|設定這個目標輸出裝置`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetTextMode](#settextmode)|設定 rich edit 控制項的文字模式或復原層級。 如果控制項包含文字，訊息將會失敗。|  
|[CRichEditCtrl::SetUndoLimit](#setundolimit)|設定的動作所儲存的復原佇列的數目上限。|  
|[CRichEditCtrl::SetWordCharFormat](#setwordcharformat)|設定格式屬性，這在目前的文字中的字元`CRichEditCtrl`物件。|  
|[CRichEditCtrl::SetWordWrapMode](#setwordwrapmode)|豐富的文字換行和斷詞選項集的編輯控制項。 這個訊息是作業系統的僅適用於亞洲語言版本。|  
|[CRichEditCtrl::StopGroupTyping](#stopgrouptyping)|停止控制項收集其他輸入目前的復原動作的動作。 控制項在合併為一個新的動作復原佇列中的任何儲存的下一個輸入動作。|  
|[CRichEditCtrl::StreamIn](#streamin)|這會將文字插入輸入資料流`CRichEditCtrl`物件。|  
|[CRichEditCtrl::StreamOut](#streamout)|將文字從這個儲存`CRichEditCtrl`輸出資料流中的物件。|  
|[CRichEditCtrl::Undo](#undo)|復原上次的編輯作業。|  
  
## <a name="remarks"></a>備註  
 「 Rich edit 控制項 」 是一個視窗，讓使用者輸入及編輯文字。 文字字元和段落格式，可以指派，而且可以包含內嵌的 OLE 物件。 Rich edit 控制項來格式化文字，提供程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。  
  
 這個 Windows 通用控制項 (並因此`CRichEditCtrl`類別) 僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 下執行的程式和更新版本。 `CRichEditCtrl`類別可支援的版本 2.0 和 3.0 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] rich edit 控制項。  
  
> [!CAUTION]
>  如果您使用 rich edit 控制項在對話方塊中 (不論是否有您的應用程式是 SDI、 MDI 或對話方塊架構)，您必須呼叫[AfxInitRichEdit](application-information-and-management.md#afxinitrichedit)之後顯示之前的對話方塊。 呼叫這個函式的一般位置是在程式的 `InitInstance` 成員函式中。 只需在第一次顯示對話方塊時呼叫它一次。 如果您使用 `AfxInitRichEdit`，不需要呼叫 `CRichEditView`。  
  
 如需有關使用`CRichEditCtrl`，請參閱︰  
  
- [控制項](../../mfc/controls-mfc.md)  
  
- [使用 CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   知識庫文件 Q259949︰ 資訊︰ SetCaretPos() 是不適當與 CEdit 或 CRichEditCtrl 控制項  
  
 在 MFC 應用程式中使用 rich edit 控制項的範例，請參閱[WORDPAD](../../visual-cpp-samples.md)範例應用程式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="canpaste"></a>CRichEditCtrl::CanPaste  
 判斷 rich edit 控制項可以貼上指定的剪貼簿格式。  
  
```  
BOOL CanPaste(UINT nFormat = 0) const;  
```  
  
### <a name="parameters"></a>參數  
 `nFormat`  
 要查詢的剪貼簿資料格式。 這個參數可以是其中一個預先定義的剪貼簿格式或所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)。  
  
### <a name="return-value"></a>傳回值  
 非零，如果可以貼上剪貼簿格式。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`nFormat`為 0，`CanPaste`將重試目前的剪貼簿的任何格式。  
  
 如需詳細資訊，請參閱[EM_CANPASTE](http://msdn.microsoft.com/library/windows/desktop/bb787993)訊息和[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&1;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_1.cpp)]  
  
##  <a name="canredo"></a>CRichEditCtrl::CanRedo  
 判斷是否重做佇列包含的任何動作。  
  
```  
BOOL CanRedo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果重做佇列包含動作，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 若要找到重做佇列中作業的名稱，請呼叫[CRichEditCtrl::GetRedoName](#getredoname)。 若要取消復原最新的復原作業，請呼叫[重做](#redo)。  
  
 如需詳細資訊，請參閱[EM_CANREDO](http://msdn.microsoft.com/library/windows/desktop/bb787995)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="canundo"></a>CRichEditCtrl::CanUndo  
 決定是否可以復原上次的編輯作業。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果呼叫復原上次的編輯作業為非零[復原](#undo)成員函式，則為 0，如果無法復原。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&2;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_2.cpp)]  
  
##  <a name="charfrompos"></a>CRichEditCtrl::CharFromPos  
 擷取參數所指定的點字元的相關資訊`pt`。  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含指定點的座標。  
  
### <a name="return-value"></a>傳回值  
 最接近指定點的字元以零為起始的字元索引。 如果指定的點超出控制項中的最後一個字元，傳回的值會指出控制項中的最後一個字元。  
  
### <a name="remarks"></a>備註  
 此成員函式搭配使用 rich edit 控制項。 若要取得編輯控制項的資訊，請呼叫[CEdit::CharFromPos](../../mfc/reference/cedit-class.md#charfrompos)。  
  
 如需詳細資訊，請參閱[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="clear"></a>CRichEditCtrl::Clear  
 （清除） 會刪除目前選取範圍 （如果有的話） 在 rich edit 控制項。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 刪除由**清除**可以藉由呼叫復原[復原](#undo)成員函式。  
  
 若要刪除目前選取範圍，並將已刪除的內容到剪貼簿，呼叫[剪下](#cut)成員函式。  
  
 如需詳細資訊，請參閱[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&3;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_3.cpp)]  
  
##  <a name="copy"></a>CRichEditCtrl::Copy  
 複製目前的選取範圍 （如果有的話） 在 rich edit 控制項到剪貼簿。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&4;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_4.cpp)]  
  
##  <a name="create"></a>CRichEditCtrl::Create  
 建立 Windows rich edit 控制項，並將它與此相關聯`CRichEditCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定編輯控制項的樣式。 套用所列出的視窗樣式的組合**備註**節 < 和[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定編輯控制項的大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](../../mfc/reference/rect-structure1.md)結構。  
  
 `pParentWnd`  
 指定編輯控制項的父視窗 (通常[CDialog](../../mfc/reference/cdialog-class.md))。 它不得為**NULL**。  
  
 `nID`  
 指定編輯控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CRichEditCtrl`兩個步驟中的物件。 首先，呼叫[CRichEditCtrl](#cricheditctrl)建構函式，然後呼叫**建立**，其建立 Windows 編輯控制項，並將它附加`CRichEditCtrl`物件。  
  
 當您建立與這個函式的 rich edit 控制項時，首先您必須載入必要的通用控制項程式庫。 若要載入程式庫，呼叫全域函式[AfxInitRichEdit](application-information-and-management.md#afxinitrichedit)，這會初始化通用控制項程式庫。 您需要呼叫`AfxInitRichEdit`程序中的只能出現一次。  
  
 當**建立**執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)編輯控制項的訊息。  
  
 根據預設，處理這些訊息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式中`CWnd`基底類別。 若要擴充的預設訊息處理，衍生自`CRichEditCtrl`、 將訊息對應新增至新的類別，並覆寫上述的訊息處理常式成員函式。 覆寫`OnCreate`，例如，執行所需的初始化新的類別。  
  
 適用於下列[視窗樣式](../../mfc/reference/window-styles.md)來編輯控制項。  
  
- **WS_CHILD**一律。  
  
- **WS_VISIBLE**通常。  
  
- **WS_DISABLED**很少。  
  
- **WS_GROUP**控制項群組。  
  
- **WS_TABSTOP**包含編輯控制項的定位順序。  
  
 如需詳細的視窗樣式的詳細資訊，請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&5;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_5.cpp)]  
  
##  <a name="createex"></a>CRichEditCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CRichEditCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定編輯控制項的樣式。 套用所列出的視窗樣式的組合**備註**區段[建立](#create)和[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是**建立**套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
##  <a name="cricheditctrl"></a>CRichEditCtrl::CRichEditCtrl  
 建構 `CRichEditCtrl` 物件。  
  
```  
CRichEditCtrl();
```  
  
### <a name="remarks"></a>備註  
 使用[建立](#create)來建構 Windows rich edit 控制項。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&6;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_6.cpp)]  
  
##  <a name="cut"></a>CRichEditCtrl::Cut  
 刪除 （剪下） 編輯控制項中目前選取範圍 （如果有的話） 的豐富，而且會將已刪除的文字複製到剪貼簿。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>備註  
 刪除由**剪下**可以藉由呼叫復原[復原](#undo)成員函式。  
  
 若要刪除目前選取範圍，而不將已刪除的文字放入剪貼簿，呼叫[清除](#clear)成員函式。  
  
 如需詳細資訊，請參閱[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&7;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_7.cpp)]  
  
##  <a name="displayband"></a>CRichEditCtrl::DisplayBand  
 顯示部分內容的 rich edit 控制項 （文字和 OLE 項目），如先前所格式化[FormatRange](#formatrange)。  
  
```  
BOOL DisplayBand(LPRECT pDisplayRect);
```  
  
### <a name="parameters"></a>參數  
 `pDisplayRect`  
 指標[RECT](../../mfc/reference/rect-structure1.md)或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定要將文字顯示裝置的區域。  
  
### <a name="return-value"></a>傳回值  
 如果格式化的文字顯示執行成功，否則 0 為非零。  
  
### <a name="remarks"></a>備註  
 文字和 OLE 項目會裁剪為指標指定的區域`pDisplayRect`。  
  
 如需詳細資訊，請參閱[EM_DISPLAYBAND](http://msdn.microsoft.com/library/windows/desktop/bb787997)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditCtrl::FormatRange](#formatrange)。  
  
##  <a name="emptyundobuffer"></a>CRichEditCtrl::EmptyUndoBuffer  
 （清除） 會重設此 rich edit 控制項的復原旗標。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>備註  
 控制項現在無法復原上次的編輯作業。 Rich edit 控制項中的作業可以復原時，設定復原旗標。  
  
 每當您呼叫時，就會自動清除復原旗標[CWnd](../../mfc/reference/cwnd-class.md)成員函式[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
 如需詳細資訊，請參閱[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&8;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_8.cpp)]  
  
##  <a name="findtext"></a>CRichEditCtrl::FindText  
 尋找 rich edit 控制項中的文字。  
  
```  
long FindText(
    DWORD dwFlags,  
    FINDTEXTEX* pFindText) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 如需可能的值，請參閱`wParam`中[EM_FINDTEXTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788011)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *pFindText*  
 指標[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)結構提供參數給搜尋並傳回了找到相符的範圍。  
  
### <a name="return-value"></a>傳回值  
 以零為起始的字元位置的下一個相符項目。– 1，表示有沒有相符項目。  
  
### <a name="remarks"></a>備註  
 您可以搜尋向上或向下中設定適當的範圍參數[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構內**FINDTEXTEX**結構。  
  
 如需詳細資訊，請參閱[EM_FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb788011)訊息和[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&9;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_9.cpp)]  
  
##  <a name="findwordbreak"></a>CRichEditCtrl::FindWordBreak  
 之前或之後所指定的位置尋找下一個斷`nStart`。  
  
```  
DWORD FindWordBreak(
    UINT nCode,  
    DWORD nStart) const;  
```  
  
### <a name="parameters"></a>參數  
 `nCode`  
 表示要採取的動作。 如需可能值的清單，請參閱參數的描述`code`中**EM_FINDWORDBREAK**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nStart`  
 開始處之以零為起始的字元位置。  
  
### <a name="return-value"></a>傳回值  
 根據參數`nCode`。 如需詳細資訊，請參閱[EM_FINDWORDBREAK](http://msdn.microsoft.com/library/windows/desktop/bb788018)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 您可以使用此成員函式來擷取位於指定位置的字元的相關資訊。  
  
##  <a name="formatrange"></a>CRichEditCtrl::FormatRange  
 設定特定裝置的 rich edit 控制項中的文字範圍的格式。  
  
```  
long FormatRange(
    FORMATRANGE* pfr,  
    BOOL bDisplay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pfr*  
 指標[FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)結構，其中包含輸出裝置的相關資訊。 **NULL**指出可釋出 rich edit 控制項中的快取的資訊。  
  
 *bDisplay*  
 指出是否應該轉譯文字。 如果**FALSE**，只測量的文字。  
  
### <a name="return-value"></a>傳回值  
 適合於地區加一的最後一個字元索引。  
  
### <a name="remarks"></a>備註  
 一般而言，此呼叫後面呼叫[DisplayBand](#displayband)。  
  
 如需詳細資訊，請參閱[EM_FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb788020)訊息和[FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&10;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_10.cpp)]  
  
##  <a name="getcharpos"></a>CRichEditCtrl::GetCharPos  
 取得指定的字元在這個位置 （左上角）`CRichEditCtrl`物件。  
  
```  
CPoint GetCharPos(long lChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `lChar`  
 以零為起始的字元索引。  
  
### <a name="return-value"></a>傳回值  
 所指定的字元的左上角的位置`lChar`。  
  
### <a name="remarks"></a>備註  
 藉由以零為起始的索引值會指定字元。 如果`lChar`大於最後一個字元在這個索引`CRichEditCtrl`物件，傳回的值在此指定正好超過最後一個字元的字元位置的座標`CRichEditCtrl`物件。  
  
 如需詳細資訊，請參閱[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getdefaultcharformat"></a>CRichEditCtrl::GetDefaultCharFormat  
 取得格式設定這個屬性的預設字元`CRichEditCtrl`物件。  
  
```  
DWORD GetDefaultCharFormat(CHARFORMAT& cf) const;  DWORD GetDefaultCharFormat(CHARFORMAT2& cf) const;  ```  
  
### Parameters  
 `cf`  
 In the first version, a pointer to a **CHARFORMAT** structure holding the default character formatting attributes.  
  
 In the second version, a pointer to a **CHARFORMAT2** structure, which is a Rich Edit 2.0 extension to the **CHARFORMAT** structure, holding the default character formatting attributes.  
  
### Return Value  
 The **dwMask** data member of `cf`. It specified the default character formatting attributes.  
  
### Remarks  
 For more information, see the **EM_GETCHARFORMAT** message and the **CHARFORMAT** and **CHARFORMAT2** structures in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [SetDefaultCharFormat](#setdefaultcharformat).  
  
##  <a name="geteventmask"></a>  CRichEditCtrl::GetEventMask  
 Gets the event mask for this `CRichEditCtrl` object.  
  
```  
長 GetEventMask() const;  
```  
  
### Return Value  
 The event mask for this `CRichEditCtrl` object.  
  
### Remarks  
 The event mask specifies which notification messages the `CRichEditCtrl` object sends to its parent window.  
  
 For more information, see [EM_GETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb788032) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [CRichEditCtrl::SetEventMask](#seteventmask).  
  
##  <a name="getfirstvisibleline"></a>  CRichEditCtrl::GetFirstVisibleLine  
 Determines the topmost visible line in this `CRichEditCtrl` object.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### Return Value  
 Zero-based index of the uppermost visible line in this `CRichEditCtrl` object.  
  
### Remarks  
 For more information, see [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#11](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_11.cpp)]  
  
##  <a name="getiricheditole"></a>  CRichEditCtrl::GetIRichEditOle  
 Accesses the **IRichEditOle** interface for this `CRichEditCtrl` object.  
  
```  
IRichEditOle * GetIRichEditOle() const;  
```  
  
### Return Value  
 Pointer to the [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) interface that can be used to access this `CRichEditCtrl` object's OLE functionality; **NULL** if the interface is not accessible.  
  
### Remarks  
 Use this interface to access this `CRichEditCtrl` object's OLE functionality.  
  
 For more information, see [EM_GETOLEINTERFACE](http://msdn.microsoft.com/library/windows/desktop/bb788041) message and [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) interface in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getlimittext"></a>  CRichEditCtrl::GetLimitText  
 Gets the text limit for this `CRichEditCtrl` object.  
  
```  
長 GetLimitText() const;  
```  
  
### Return Value  
 The current text limit, in bytes, for this `CRichEditCtrl` object.  
  
### Remarks  
 The text limit is the maximum amount of text, in bytes, the rich edit control can accept.  
  
 For more information, see [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#12](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_12.cpp)]  
  
##  <a name="getline"></a>  CRichEditCtrl::GetLine  
 Retrieves a line of text from this `CRichEditCtrl` object.  
  
```  
GetLine (int nIndex，int  
    LPTSTR lpszBuffer) const;  
  
GetLine (int nIndex，int  
    LPTSTR lpszBuffer  
    int nMaxLength) const;  
```  
  
### Parameters  
 `nIndex`  
 Zero-based index of the line to retrieve.  
  
 `lpszBuffer`  
 Points to the buffer to receive the text. The first word of the buffer must specify the maximum number of bytes that can be copied into the buffer.  
  
 `nMaxLength`  
 Maximum number of characters that can be copied into `lpszBuffer`. The second form of `GetLine` places this value into the first word of the buffer specified by `lpszBuffer`.  
  
### Return Value  
 The number of characters copied into `lpszBuffer`.  
  
### Remarks  
 The copied line does not contain a terminating null character.  
  
> [!NOTE]
>  Because the first word of the buffer stores the number of characters to be copied, make sure that your buffer is at least 4 bytes long.  
  
 For more information, see [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>  CRichEditCtrl::GetLineCount  
 Retrieves the number of lines in the `CRichEditCtrl` object.  
  
```  
int GetLineCount() const;  
```  
  
### Return Value  
 The number of lines in this `CRichEditCtrl` object.  
  
### Remarks  
 For more information, see [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#13](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_13.cpp)]  
  
##  <a name="getmodify"></a>  CRichEditCtrl::GetModify  
 Determines if the contents of this `CRichEditCtrl` object have been modified.  
  
```  
BOOL GetModify() const;  
```  
  
### Return Value  
 Nonzero if the text in this `CRichEditCtrl` object has been modified; otherwise 0.  
  
### Remarks  
 Windows maintains an internal flag indicating whether the contents of the rich edit control have been changed. This flag is cleared when the edit control is first created and can also be cleared by calling the [SetModify](#setmodify) member function.  
  
 For more information, see [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#14](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_14.cpp)]  
  
##  <a name="getoptions"></a>  CRichEditCtrl::GetOptions  
 Retrieves the options currently set for the rich edit control.  
  
```  
UINT GetOptions() const;  
```  
  
### Return Value  
 A combination of the current option flag values. For a list of these values, see the *fOptions* parameter in the [EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254) message, as described in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getparaformat"></a>  CRichEditCtrl::GetParaFormat  
 Gets the paragraph formatting attributes of the current selection.  
  
```  
DWORD GetParaFormat(PARAFORMAT& pf) const; DWORD GetParaFormat(PARAFORMAT2& pf) const; ```  
  
### <a name="parameters"></a>參數  
 `pf`  
 在第一個版本中，指標[PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)結構來保留的段落格式化目前選取範圍的屬性。  
  
 在第二個版本中，指標[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)結構，這是一個豐富的編輯 2.0 擴充功能至**PARAFORMAT**結構中，保留預設字元格式的屬性。  
  
### <a name="return-value"></a>傳回值  
 **DwMask**資料成員的`pf`。 它會指定的段落格式目前的選取範圍中一致的屬性。  
  
### <a name="remarks"></a>備註  
 如果選取多個段落，`pf`收到的第一個選取的段落屬性。 傳回值指定選取範圍中一致的屬性。  
  
 如需詳細資訊，請參閱[EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182)訊息和**PARAFORMAT**和**PARAFORMAT2**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditCtrl::SetParaFormat](#setparaformat)。  
  
##  <a name="getpunctuation"></a>CRichEditCtrl::GetPunctuation  
 Rich edit 控制項中取得目前的標點符號字元。  
  
```  
BOOL GetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc) const;  
```  
  
### <a name="parameters"></a>參數  
 `fType`  
 標點符號類型旗標，如述`fType`參數[EM_GETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774184)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpPunc`  
 指標[標點符號](http://msdn.microsoft.com/library/windows/desktop/bb787944)結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 此成員函式適用於只有亞洲語言版本的作業系統。  
  
##  <a name="getrect"></a>CRichEditCtrl::GetRect  
 這會擷取格式化矩形`CRichEditCtrl`物件。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md)或指標[RECT](../../mfc/reference/rect-structure1.md)接收格式化這個矩形`CRichEditCtrl`物件。  
  
### <a name="remarks"></a>備註  
 格式化矩形是文字的週框矩形。 這個值是獨立的大小的`CRichEditCtrl`物件。  
  
 如需詳細資訊，請參閱[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[LimitText](#limittext)。  
  
##  <a name="getredoname"></a>CRichEditCtrl::GetRedoName  
 如果有的話，擷取下一個可用的動作重做佇列中的類型。  
  
```  
UNDONAMEID GetRedoName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，`GetRedoName`傳回[UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365)列舉型別，表示控制項的重做佇列中的下一個動作的類型。 如果重做佇列是空的或在佇列中的重做動作是未知的類型，`GetRedoName`會傳回 0。  
  
### <a name="remarks"></a>備註  
 復原或重做的動作類型包括輸入、 刪除、 拖放、 剪下和貼上作業。 這項資訊可讓應用程式提供擴充的使用者介面進行復原和取消復原作業，例如 redoable 動作的下拉式清單方塊。  
  
##  <a name="getsel"></a>CRichEditCtrl::GetSel  
 擷取目前的選取範圍，在此範圍`CRichEditCtrl`物件。  
  
```  
void GetSel(CHARRANGE& cr) const;  
  
void GetSel(
    long& nStartChar,  
    long& nEndChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 若要參考[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構，以接收目前選取的界限。  
  
 `nStartChar`  
 目前的選取範圍中的第一個字元之以零起始的索引。  
  
 `nEndChar`  
 目前的選取範圍的最後一個字元的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 此函式的兩種形式提供取得選取範圍的替代方式。 請遵循這些形式的簡短描述︰  
  
- **GetSel (** `cr` **)**這個表單用**CHARRANGE**結構和其**cpMin**和**cpMax**成員傳回界限。  
  
- **GetSel (** `nStartChar` **，** `nEndChar` **)**這種形式的參數中傳回界限`nStartChar`和`nEndChar`。  
  
 如果選取範圍包含的所有項目開始 ( **cpMin**或`nStartChar`) 是 0，而結束 ( **cpMax**或`nEndChar`) 是-1。  
  
 如需詳細資訊，請參閱[EM_EXGETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788001)訊息和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&15;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_15.cpp)]  
  
##  <a name="getselectioncharformat"></a>CRichEditCtrl::GetSelectionCharFormat  
 取得字元格式化目前選取範圍的屬性。  
  
```  
DWORD GetSelectionCharFormat(CHARFORMAT& cf) const;  DWORD GetSelectionCharFormat(CHARFORMAT2& cf) const;  ```  
  
### Parameters  
 `cf`  
 In the first version, a pointer to a [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) structure to receive the character formatting attributes of the current selection.  
  
 In the second version, a pointer to a [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) structure, which is a Rich Edit 2.0 extension to the **CHARFORMAT** structure to receive the character formatting attributes of the current selection.  
  
### Return Value  
 The **dwMask** data member of `cf`. It specifies the character formatting attributes that are consistent throughout the current selection.  
  
### Remarks  
 The `cf` parameter receives the attributes of the first character in the current selection. The return value specifies which attributes are consistent throughout the selection.  
  
 For more information, see the [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) message and the **CHARFORMAT** and **CHARFORMAT2** structures in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [SetSelectionCharFormat](#setselectioncharformat).  
  
##  <a name="getselectiontype"></a>  CRichEditCtrl::GetSelectionType  
 Determines the selection type in this `CRichEditCtrl` object.  
  
```  
WORD GetSelectionType() const;  
```  
  
### Return Value  
 Flags indicating the contents of the current selection. A combination of the following flags:  
  
- `SEL_EMPTY` Indicates that there is no current selection.  
  
- `SEL_TEXT` Indicates that the current selection contains text.  
  
- `SEL_OBJECT` Indicates that the current selection contains at least one OLE item.  
  
- `SEL_MULTICHAR` Indicates that the current selection contains more than one character of text.  
  
- `SEL_MULTIOBJECT` Indicates that the current selection contains more than one OLE object.  
  
### Remarks  
 For more information, see [EM_SELECTIONTYPE](http://msdn.microsoft.com/library/windows/desktop/bb774223) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#16](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_16.cpp)]  
  
##  <a name="getseltext"></a>  CRichEditCtrl::GetSelText  
 Retrieves the text from the current selection in this `CRichEditCtrl` object.  
  
```  
長 GetSelText(LPSTR lpBuf) const; CString GetSelText() const; ```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 若要接收目前選取範圍中的文字緩衝區指標。  
  
### <a name="return-value"></a>傳回值  
 取決於形式︰  
  
- **GetSelText (** `lpBuf` **)**的字元複製到數`lpBuf`，但不包含 null 結束。  
  
- **GetSelText （)**字串，包含目前的選取範圍。  
  
### <a name="remarks"></a>備註  
 如果您使用第一個表單， **GetSelText (** `lpBuf` **)**，您必須確定緩衝區夠大，就會收到的文字。 呼叫[GetSel](#getsel)來判斷目前的選取範圍的字元數目。  
  
 如需詳細資訊，請參閱[EM_GETSELTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774190)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditCtrl::GetSelectionType](#getselectiontype)。  
  
##  <a name="gettextlength"></a>CRichEditCtrl::GetTextLength  
 擷取文字的長度，以字元為單位，在此`CRichEditCtrl`物件，不包括結束的 null 字元。  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在這個文字的長度`CRichEditCtrl`物件。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[WM_GETTEXTLENGTH](http://msdn.microsoft.com/library/windows/desktop/ms632628)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&17;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_17.cpp)]  
  
##  <a name="gettextlengthex"></a>CRichEditCtrl::GetTextLengthEx  
 計算的 rich edit 控制項中文字的長度。  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 值，指定要用來判斷文字長度的方法。 這個成員可以是其中一個或多個值中的旗標成員列出[GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `uCodePage`  
 翻譯 (CP_ACP ANSI 字碼頁，unicode 1200) 的字碼頁。  
  
### <a name="return-value"></a>傳回值  
 字元或編輯控制項中的位元組數目。 如果在已設定不相容的旗標`dwFlags`，此成員函式會傳回`E_INVALIDARG`。  
  
### <a name="remarks"></a>備註  
 `GetTextLengthEx`提供其他方法，判斷文字的長度。 它支援豐富的編輯 2.0 的功能。 請參閱[有關 Rich Edit 控制項](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="gettextmode"></a>CRichEditCtrl::GetTextMode  
 擷取目前文字模式和復原層級的 rich edit 控制項。  
  
```  
UINT GetTextMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位元旗標，從一組[TEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774364)列舉類型中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 旗標會指出目前文字模式，而且復原的控制層級。  
  
##  <a name="gettextrange"></a>CRichEditCtrl::GetTextRange  
 取得指定的字元範圍。  
  
```  
int GetTextRange(
    int nFirst,  
    int nLast,  
    CString& refString) const;  
```  
  
### <a name="parameters"></a>參數  
 `nFirst`  
 立即在範圍中之前的第一個字元的字元位置的索引。  
  
 `nLast`  
 緊接在範圍中的最後一個字元的字元位置。  
  
 `refString`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，將接收的文字。  
  
### <a name="return-value"></a>傳回值  
 複製的字元數目，不包括結束的 null 字元。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETTEXTRANGE](http://msdn.microsoft.com/library/windows/desktop/bb774199)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `GetTextRange`支援豐富的編輯 2.0 的功能。 請參閱[有關 Rich Edit 控制項](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="getundoname"></a>CRichEditCtrl::GetUndoName  
 如果有的話，擷取復原佇列中的下一個可用的動作的類型。  
  
```  
UNDONAMEID GetUndoName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果復原動作會在控制項的復原佇列中，`GetUndoName`傳回[UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365)列舉型別表示在佇列中的下一個動作的類型。 如果復原佇列是空的或在佇列中的復原動作是未知的類型，`GetUndoName`會傳回 0。  
  
### <a name="remarks"></a>備註  
 復原或重做的動作類型包括輸入、 刪除、 拖放、 剪下和貼上作業。 這項資訊可讓應用程式提供擴充的使用者介面進行復原和取消復原作業，例如可復原的動作的下拉式清單方塊。  
  
##  <a name="getwordwrapmode"></a>CRichEditCtrl::GetWordWrapMode  
 擷取目前的文字換行及 rich edit 控制項的 word 新選項。  
  
```  
UINT GetWordWrapMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的文字換行和斷詞選項。 這些選項所述[EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式是作業系統的僅適用於亞洲語言版本。  
  
##  <a name="hideselection"></a>CRichEditCtrl::HideSelection  
 變更選取範圍的可見性。  
  
```  
void HideSelection(
    BOOL bHide,  
    BOOL bPerm);
```  
  
### <a name="parameters"></a>參數  
 `bHide`  
 指出是否選取項目應該要顯示或隱藏， **TRUE**隱藏選取範圍。  
  
 `bPerm`  
 表示此選取項目的可見性的變更是否應該永久。  
  
### <a name="remarks"></a>備註  
 當`bPerm`是**TRUE**，它會變更`ECO_NOHIDESEL`這個選項`CRichEditCtrl`物件。 此選項的簡短說明，請參閱[SetOptions](#setoptions)。 您可以使用此函式來設定所有的選項`CRichEditCtrl`物件。  
  
 如需詳細資訊，請參閱[EM_HIDESELECTION](http://msdn.microsoft.com/library/windows/desktop/bb774210)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&18;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_18.cpp)]  
  
##  <a name="limittext"></a>CRichEditCtrl::LimitText  
 限制使用者可以編輯控制項中輸入文字的長度。  
  
```  
void LimitText(long nChars = 0);
```  
  
### <a name="parameters"></a>參數  
 `nChars`  
 指定使用者可以輸入之文字的長度 （以位元組為單位）。 如果此參數為 0 （預設值），文字長度會設定為 64k 個位元組。  
  
### <a name="remarks"></a>備註  
 變更文字的限制會限制只顯示使用者可以輸入的文字。 它有任何文字不會影響已經在編輯控制項中，也不會影響編輯控制項所複製的文字長度[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項的呼叫中指定以外置於`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者使用新的文字來取代現有的文字，除非刪除目前選取範圍會造成要低於文字限制的文字。  
  
> [!NOTE]
>  對於文字限制，每個 OLE 項目都會計算為單一字元。  
  
 如需詳細資訊，請參閱[EM_EXLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788003)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&19;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_19.cpp)]  
  
##  <a name="linefromchar"></a>CRichEditCtrl::LineFromChar  
 擷取包含指定之的字元索引的那一行的行號。  
  
```  
long LineFromChar(long nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 包含編輯控制項的文字中所需的字元以零為起始的索引值，或包含-1。 如果`nIndex`為 –&1;，它會指定目前的行，也就是包含游標的那一行。  
  
### <a name="return-value"></a>傳回值  
 包含所指定的字元索引的行的以零為起始的行號`nIndex`。 如果`nIndex`為 –&1;，會傳回包含選取範圍的第一個字元的行號。 如果沒有選取範圍，則會傳回目前的行號。  
  
### <a name="remarks"></a>備註  
 字元索引是從 rich edit 控制項的開頭的字元數。 為字元計數，OLE 項目會視為單一字元。  
  
 如需詳細資訊，請參閱[EM_EXLINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb788005)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&20;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_20.cpp)]  
  
##  <a name="lineindex"></a>CRichEditCtrl::LineIndex  
 擷取在這一行的字元索引`CRichEditCtrl`物件。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nLine`  
 包含要在編輯控制項的文字行的索引值，或包含-1。 如果`nLine`為 –&1;，它會指定目前的行，也就是包含游標的那一行。  
  
### <a name="return-value"></a>傳回值  
 在指定的行的字元索引`nLine`或-1，如果指定的列數，然後編輯控制項中的行數。  
  
### <a name="remarks"></a>備註  
 字元索引是指定線條的起點的 rich edit 控制項的字元數。  
  
 如需詳細資訊，請參閱[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&21;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_21.cpp)]  
  
##  <a name="linelength"></a>CRichEditCtrl::LineLength  
 擷取 rich edit 控制項中的資料行的長度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `nLine`  
 其長度是要擷取的列中指定字元的字元索引。 如果此參數為 –&1;，則會傳回目前的行 （包含插入號的那一行） 的長度，不包括任何長度已選取的文字行中。 當`LineLength`稱為單行編輯控制項，會忽略此參數。  
  
### <a name="return-value"></a>傳回值  
 當`LineLength`稱為對於多行編輯控制項，傳回的值是由指定的行長度 （以位元組為單位） `nLine`。 當`LineLength`稱為單行編輯控制項，傳回的值是在編輯控制項中文字的長度 （以位元組為單位）。  
  
### <a name="remarks"></a>備註  
 使用[LineIndex](#lineindex)成員函式，以取得在這個特定的行號的字元索引`CRichEditCtrl`物件。  
  
 如需詳細資訊，請參閱[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[LineIndex](#lineindex)。  
  
##  <a name="linescroll"></a>CRichEditCtrl::LineScroll  
 捲動多行編輯控制項的文字。  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>參數  
 `nLines`  
 指定要垂直捲動行的數。  
  
 `nChars`  
 指定要水平捲動字元位置的數目。 如果 rich edit 控制項已經忽略這個值**ES_RIGHT**或**ES_CENTER**樣式。 [編輯樣式](../../mfc/reference/edit-styles.md)中所指定[建立](#create)。  
  
### <a name="remarks"></a>備註  
 編輯控制項不會以垂直方式捲動，過去的文字編輯控制項中的最後一行。 如果目前的行加上所指定的行數`nLines`超過編輯控制項中的總行數，值會調整，使編輯控制項的最後一行捲動到 編輯控制項視窗的頂端。  
  
 `LineScroll`可以用於水平捲動過去的任何一行的最後一個字元。  
  
 如需詳細資訊，請參閱[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="paste"></a>CRichEditCtrl::Paste  
 將資料從剪貼簿`CRichEditCtrl`插入點，插入號位置。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>備註  
 只有當剪貼簿包含可辨識的格式的資料插入資料。  
  
 如需詳細資訊，請參閱[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&22;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_22.cpp)]  
  
##  <a name="pastespecial"></a>CRichEditCtrl::PasteSpecial  
 將資料貼到這個特定的剪貼簿格式`CRichEditCtrl`物件。  
  
```  
void PasteSpecial(
    UINT nClipFormat,  
    DWORD dvAspect = 0,  
    HMETAFILE hMF = 0);
```  
  
### <a name="parameters"></a>參數  
 *nClipFormat*  
 剪貼簿格式貼到這`CRichEditCtrl`物件。  
  
 *dvAspect*  
 若要從剪貼簿擷取資料的裝置層面。  
  
 *hMF*  
 包含要貼上物件的 [圖示] 檢視的中繼檔的控制代碼。  
  
### <a name="remarks"></a>備註  
 插入點，插入號位置插入新的資料。  
  
 如需詳細資訊，請參閱[EM_PASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/bb774214)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&23;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_23.cpp)]  
  
##  <a name="posfromchar"></a>CRichEditCtrl::PosFromChar  
 擷取指定的字元，在編輯控制項中的用戶端區域座標。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 字元以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 字元，（x，y） 的位置。 對於單一行編輯控制項，y 軸座標永遠是零。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="redo"></a>CRichEditCtrl::Redo  
 取消復原上控制項的重做佇列中的下一個動作。  
  
```  
BOOL Redo();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_REDO](http://msdn.microsoft.com/library/windows/desktop/bb774218)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="replacesel"></a>CRichEditCtrl::ReplaceSel  
 取代目前的選取範圍，在此`CRichEditCtrl`含有指定文字的物件。  
  
```  
void ReplaceSel(
    LPCTSTR lpszNewText,  
    BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `lpszNewText`  
 以 null 終止的字串，包含取代文字指標。  
  
 `bCanUndo`  
 若要指定可以復原此函式，來設定此參數，以值**TRUE**。 預設值是**FALSE**。  
  
### <a name="remarks"></a>備註  
 要取代此中的所有文字`CRichEditCtrl`物件，請使用[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
 如果沒有目前選取範圍，取代文字會插入在插入點，也就是目前插入號位置。  
  
 此函式將現有的字元格式格式化插入的文字。 取代文字的整個範圍時 (藉由呼叫`SetSel`（0，-1） 之前，先呼叫`ReplaceSel`)，沒有結尾段落字元會保留之前的段落格式，在新插入的文字所繼承而來。  
  
 如需詳細資訊，請參閱[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[LineIndex](#lineindex)。  
  
##  <a name="requestresize"></a>CRichEditCtrl::RequestResize  
 這會強制`CRichEditCtrl`物件傳送**EN_REQUESTRESIZE**通知訊息至其父視窗。  
  
```  
void RequestResize();
```  
  
### <a name="remarks"></a>備註  
 此函式可以在[CWnd::OnSize](../../mfc/reference/cwnd-class.md#onsize)處理無底邊`CRichEditCtrl`物件。  
  
 如需詳細資訊，請參閱[EM_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb774220)訊息和**無底邊 Rich Edit 控制項**區段[有關 Rich Edit 控制項](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setautourldetect"></a>CRichEditCtrl::SetAutoURLDetect  
 設定自動偵測 URL 的 rich edit 控制項。  
  
```  
BOOL SetAutoURLDetect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 指定是否要將控制項設定為自動偵測的 URL。 如果**TRUE**，它會啟用。 如果**FALSE**，就會停用。  
  
### <a name="return-value"></a>傳回值  
 如果成功，否則為非零值是零。 例如，訊息可能會失敗，因為記憶體不足。  
  
### <a name="remarks"></a>備註  
 如果啟用，rich edit 控制項將掃描來判斷它是否符合標準的 URL 格式的文字。 如需這些 URL 格式，請參閱[EM_AUTOURLDETECT](http://msdn.microsoft.com/library/windows/desktop/bb787991)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  請勿設定`SetAutoURLDetect`至**TRUE**如果您編輯的控制項使用**CFE_LINK**以外 Url 文字的效果。 `SetAutoURLDetect`url 會啟用這個效果，則會停用所有其他文字。 請參閱[EN_LINK](http://msdn.microsoft.com/library/windows/desktop/bb787970)如需詳細資訊**CFE_LINK**效果。  
  
##  <a name="setbackgroundcolor"></a>CRichEditCtrl::SetBackgroundColor  
 此設定的背景色彩`CRichEditCtrl`物件。  
  
```  
COLORREF SetBackgroundColor(
    BOOL bSysColor,  
    COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `bSysColor`  
 表示系統值，應該先設定背景色彩。 如果這個值是**TRUE**，`cr`會被忽略。  
  
 `cr`  
 要求的背景色彩。 使用的才`bSysColor`是**FALSE**。  
  
### <a name="return-value"></a>傳回值  
 先前的背景色彩，此`CRichEditCtrl`物件。  
  
### <a name="remarks"></a>備註  
 系統值或指定，就可以設定的背景色彩[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。  
  
 如需詳細資訊，請參閱[EM_SETBKGNDCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774228)訊息和[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&24;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_24.cpp)]  
  
##  <a name="setdefaultcharformat"></a>CRichEditCtrl::SetDefaultCharFormat  
 設定格式屬性，在此新文字的字元`CRichEditCtrl`物件。  
  
```  
BOOL SetDefaultCharFormat(CHARFORMAT& cf);  
BOOL SetDefaultCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 在第一個版本中，指標[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)結構，其中包含新的預設字元格式的屬性。  
  
 在第二個版本中，指標[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構，這是一個豐富的編輯 2.0 擴充功能至**CHARFORMAT**結構，包含預設字元格式的屬性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 只有屬性所指定**dwMask**成員`cf`中變更此函式。  
  
 如需詳細資訊，請參閱[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)訊息和**CHARFORMAT**和**CHARFORMAT2**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&25;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_25.cpp)]  
  
##  <a name="seteventmask"></a>CRichEditCtrl::SetEventMask  
 設定這個事件遮罩`CRichEditCtrl`物件。  
  
```  
DWORD SetEventMask(DWORD dwEventMask);
```  
  
### <a name="parameters"></a>參數  
 *dwEventMask*  
 這個新的事件遮罩`CRichEditCtrl`物件。  
  
### <a name="return-value"></a>傳回值  
 先前的事件遮罩。  
  
### <a name="remarks"></a>備註  
 事件遮罩指定通知訊息`CRichEditCtrl`物件傳送至其父視窗。  
  
 如需詳細資訊，請參閱[EM_SETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb774238)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&26;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_26.cpp)]  
  
##  <a name="setmodify"></a>CRichEditCtrl::SetModify  
 設定或清除編輯控制項的已修改旗標。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bModified`  
 值為**TRUE**表示文字已修改，而值為**FALSE**指出它是未經修改。 根據預設，會設定已修改的旗標。  
  
### <a name="remarks"></a>備註  
 修改過的旗標會指出已修改的文字編輯控制項中。 它會自動設定每次使用者變更文字。 其值可以擷取與[GetModify](#getmodify)成員函式。  
  
 如需詳細資訊，請參閱[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[GetModify](#getmodify)。  
  
##  <a name="setolecallback"></a>CRichEditCtrl::SetOLECallback  
 提供此`CRichEditCtrl`物件**IRichEditOleCallback**物件，用來存取 OLE 相關資源和資訊。  
  
```  
BOOL SetOLECallback(IRichEditOleCallback* pCallback);
```  
  
### <a name="parameters"></a>參數  
 `pCallback`  
 指標[IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308)物件這`CRichEditCtrl`物件會使用以 OLE 相關資源和資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這`CRichEditCtrl`物件會呼叫[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)遞增所指定的 COM 物件的使用計數`pCallback`。  
  
 如需詳細資訊，請參閱[EM_SETOLECALLBACK](http://msdn.microsoft.com/library/windows/desktop/bb774252)訊息和[IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308)介面[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setoptions"></a>CRichEditCtrl::SetOptions  
 設定這個選項`CRichEditCtrl`物件。  
  
```  
void SetOptions(
    WORD wOp,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>參數  
 *wOp*  
 指出作業的類型。 下列其中一個值：  
  
- `ECOOP_SET`將選項設定為所指定的`dwFlags`。  
  
- `ECOOP_OR`目前的選項結合所指定的`dwFlags`。  
  
- `ECOOP_AND`保留只有目前的選項，也由`dwFlags`。  
  
- `ECOOP_XOR`保留只有目前的選項，是*不*所指定`dwFlags`。  
  
 `dwFlags`  
 豐富的編輯選項。 旗標值詳列於 < 備註 > 一節。  
  
### <a name="remarks"></a>備註  
 選項可以是下列值的組合︰  
  
- `ECO_AUTOWORDSELECTION`自動文字選取項目上的按兩下。  
  
- `ECO_AUTOVSCROLL`當使用者輸入的行結尾字元，會自動捲動 10 個字元的文字靠右。 當使用者按下 ENTER 鍵時，控制項捲動至位置為零的所有文字。  
  
- `ECO_AUTOHSCROLL`當使用者按下 ENTER 鍵的最後一行時，會自動捲動文字向上移動一個頁面。  
  
- `ECO_NOHIDESEL`否定編輯控制項的預設行為。 當控制項失去輸入的焦點，並顯示選取項目，當控制項收到輸入的焦點時，預設行為會隱藏選取範圍。 如果您指定`ECO_NOHIDESEL`，反轉選取的文字，即使控制項沒有焦點。  
  
- `ECO_READONLY`可防止使用者輸入或編輯控制項中編輯文字。  
  
- `ECO_WANTRETURN`指定當使用者按下 ENTER 鍵，同時將多行 rich edit 控制項在對話方塊中輸入文字時插入歸位字元。 如果未指定此樣式，按下 ENTER 鍵傳送命令至 rich edit 控制項的父視窗會模擬按一下父視窗的預設值 按鈕 （例如，在對話方塊中 確定 按鈕）。 此樣式影響不在單一行編輯控制項。  
  
- `ECO_SAVESEL`當控制項失去焦點時，會保留選取項目。 根據預設，當它重新取得焦點時，會選取控制項的整個內容。  
  
- `ECO_VERTICAL`以垂直方向繪製文字和物件。 適用於亞洲語言的語言。  
  
 如需詳細資訊，請參閱[EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&27;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_27.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditCtrl::SetParaFormat  
 設定段落格式屬性目前的選取範圍，在此`CRichEditCtrl`物件。  
  
```  
BOOL SetParaFormat(PARAFORMAT& pf);  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>參數  
 `pf`  
 在第一個版本中，指標[PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)結構，其中包含新的預設段落格式屬性。  
  
 在第二個版本中，指標[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)結構，這是一個豐富的編輯 2.0 擴充功能至**PARAFORMAT**結構中，保留預設字元格式的屬性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 只有屬性所指定**dwMask**成員`pf`中變更此函式。  
  
 如需詳細資訊，請參閱[EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276)訊息和**PARAFORMAT**和**PARAFORMAT2**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&28;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_28.cpp)]  
  
##  <a name="setpunctuation"></a>CRichEditCtrl::SetPunctuation  
 Rich edit 控制項中設定的標點符號。  
  
```  
BOOL SetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc);
```  
  
### <a name="parameters"></a>參數  
 `fType`  
 標點符號的旗標。 如需可能的值，請參閱`fType`參數[EM_SETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774278)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpPunc`  
 指標[標點符號](http://msdn.microsoft.com/library/windows/desktop/bb787944)結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式適用於只有亞洲語言版本的作業系統。  
  
##  <a name="setreadonly"></a>CRichEditCtrl::SetReadOnly  
 變更`ECO_READONLY`選項`CRichEditCtrl`物件。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bReadOnly`  
 表示如果這個`CRichEditCtrl`物件應該唯讀。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此選項的簡短說明，請參閱[SetOptions](#setoptions)。 您可以使用此函式來設定所有的選項`CRichEditCtrl`物件。  
  
 如需詳細資訊，請參閱[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&29;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_29.cpp)]  
  
##  <a name="setrect"></a>CRichEditCtrl::SetRect  
 設定這個格式化矩形`CRichEditCtrl`物件。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md)或指標[RECT](../../mfc/reference/rect-structure1.md) ，指出格式化的矩形的新界限。  
  
### <a name="remarks"></a>備註  
 格式化矩形是文字的限制矩形。 Rich edit 控制項視窗的大小限制的矩形無關。 當這`CRichEditCtrl`第一次建立物件，格式化矩形是相同的工作區視窗的大小。 使用`SetRect`大於或小於豐富的編輯視窗進行格式化的矩形。  
  
 如需詳細資訊，請參閱[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&30;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_30.cpp)]  
  
##  <a name="setsel"></a>CRichEditCtrl::SetSel  
 設定在這個選取項目`CRichEditCtrl`物件。  
  
```  
void SetSel(
    long nStartChar,  
    long nEndChar);  
  
void SetSel(CHARRANGE& cr);
```  
  
### <a name="parameters"></a>參數  
 `nStartChar`  
 選取範圍的第一個字元的以零為起始的索引。  
  
 `nEndChar`  
 選取範圍的最後一個字元的以零為起始的索引。  
  
 `cr`  
 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構會存放在目前選取的界限。  
  
### <a name="remarks"></a>備註  
 此函式的兩種形式提供替代方式來設定選取範圍的界限。 請遵循這些形式的簡短描述︰  
  
- **SetSel (** `cr` **)**這個表單用**CHARRANGE**結構和其**cpMin**和**cpMax**成員設定界限。  
  
- **SetSel (** `nStartChar` **，** `nEndChar` **)**此表單可以使用的參數`nStartChar`和`nEndChar`設定界限。  
  
 插入號放在以更高的啟動選取範圍結尾 ( **cpMin**或`nStartChar`) 和結束 ( **cpMax**或`nEndChar`) 的索引。 此函式將內容捲動`CRichEditCtrl`，以便顯示插入號。  
  
 若要在此選取所有文字`CRichEditCtrl`物件，請呼叫`SetSel`與 0 和結束索引為 1 的起始索引。  
  
 如需詳細資訊，請參閱[EM_EXSETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788007)訊息和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[GetSel](#getsel)。  
  
##  <a name="setselectioncharformat"></a>CRichEditCtrl::SetSelectionCharFormat  
 設定格式屬性，這在目前的選取範圍中文字的字元`CRichEditCtrl`物件。  
  
```  
BOOL SetSelectionCharFormat(CHARFORMAT& cf);  
BOOL SetSelectionCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 在第一個版本中，指標[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)結構，其中包含新的字元格式化屬性目前的選取範圍。  
  
 在第二個版本中，指標[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構，這是一個豐富的編輯 2.0 擴充功能至**CHARFORMAT**結構，包含新的字元格式化目前選取範圍的屬性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 只有屬性所指定**dwMask**成員`cf`中變更此函式。  
  
 如需詳細資訊，請參閱[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)和**CHARFORMAT**和**CHARFORMAT2**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&31;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_31.cpp)]  
  
##  <a name="settargetdevice"></a>CRichEditCtrl::SetTargetDevice  
 設定用於所見即所得的目標裝置和線條寬度 （所見即所得） 在此格式`CRichEditCtrl`物件。  
  
```  
BOOL SetTargetDevice(
    HDC hDC,  
    long lLineWidth);

 
BOOL SetTargetDevice(
    CDC& dc,  
    long lLineWidth);
```  
  
### <a name="parameters"></a>參數  
 `hDC`  
 新的目標裝置的裝置內容的控制代碼。  
  
 *lLineWidth*  
 用來格式化的線條寬度。  
  
 `dc`  
 [CDC](../../mfc/reference/cdc-class.md)新的目標裝置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此函式成功，rich edit 控制項擁有該裝置做為參數傳遞的內容。 在此情況下，呼叫的函式不應終結的裝置內容。  
  
 如需詳細資訊，請參閱[EM_SETTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/bb774282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&32;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_32.cpp)]  
  
##  <a name="settextmode"></a>CRichEditCtrl::SetTextMode  
 設定 rich edit 控制項的文字模式或復原和取消復原層級。  
  
```  
BOOL SetTextMode(UINT fMode);
```  
  
### <a name="parameters"></a>參數  
 *fMode*  
 指定控制項的文字模式和復原層級的參數的新設定。 如需可能值的清單，請參閱的模式參數[EM_SETTEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774286)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功，否則為非零值是零。  
  
### <a name="remarks"></a>備註  
 如需文字模式的說明，請參閱**EM_SETTEXTMODE**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果控制項包含文字，此成員函式將會失敗。 若要確定是空的控制項，請傳送[WM_SETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632644)訊息以空字串。  
  
##  <a name="setundolimit"></a>CRichEditCtrl::SetUndoLimit  
 設定的動作所儲存的復原佇列的數目上限。  
  
```  
UINT SetUndoLimit(UINT nLimit);
```  
  
### <a name="parameters"></a>參數  
 *nLimit*  
 指定可復原佇列中儲存的動作的數目上限。 設定為零表示停用復原。  
  
### <a name="return-value"></a>傳回值  
 新的豐富的復原動作的最大數目的編輯控制項。  
  
### <a name="remarks"></a>備註  
 根據預設，復原佇列中的動作數目上限為 100。 如果您增加這個數字時，必須有足夠的記憶體來容納新的數字。 為了達到最佳效能，設定最小可能值的限制。  
  
##  <a name="setwordcharformat"></a>CRichEditCtrl::SetWordCharFormat  
 設定格式的目前選取的文字，在這個屬性的字元`CRichEditCtrl`物件。  
  
```  
BOOL SetWordCharFormat(CHARFORMAT& cf);  
BOOL SetWordCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 在第一個版本中，指標[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)結構，其中包含新的字元格式設定屬性的目前選取的文字。  
  
 在第二個版本中，指標[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構，這是一個豐富的編輯 2.0 擴充功能至**CHARFORMAT**結構，包含格式屬性目前選取的文字換行字元。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 只有屬性所指定**dwMask**成員`cf`中變更此函式。  
  
 如需詳細資訊，請參閱[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)訊息和**CHARFORMAT**和**CHARFORMAT2**中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&33;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_33.cpp)]  
  
##  <a name="setwordwrapmode"></a>CRichEditCtrl::SetWordWrapMode  
 豐富的文字換行和斷詞選項集的編輯控制項。  
  
```  
UINT SetWordWrapMode(UINT uFlags) const;  
```  
  
### <a name="parameters"></a>參數  
 `uFlags`  
 若要設定文字換行和斷詞選項。 如需可能的選項，請參閱[EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 斷詞與目前的文字換行選項。  
  
### <a name="remarks"></a>備註  
 這個訊息是作業系統的僅適用於亞洲語言版本。  
  
##  <a name="stopgrouptyping"></a>CRichEditCtrl::StopGroupTyping  
 停止控制項收集其他輸入目前的復原動作的動作。  
  
```  
void StopGroupTyping();
```  
  
### <a name="remarks"></a>備註  
 控制項在合併為一個新的動作復原佇列中的任何儲存的下一個輸入動作。  
  
 如需詳細資訊，請參閱[EM_STOPGROUPTYPING](http://msdn.microsoft.com/library/windows/desktop/bb774300)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="streamin"></a>CRichEditCtrl::StreamIn  
 取代文字中這`CRichEditCtrl`物件與指定的輸入資料流的文字。  
  
```  
long StreamIn(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>參數  
 `nFormat`  
 旗標，指定輸入的資料格式。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `es`  
 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)結構，指定輸入資料流。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="return-value"></a>傳回值  
 從輸入資料流讀取的字元數。  
  
### <a name="remarks"></a>備註  
 值`nFormat`必須是下列其中之一︰  
  
- `SF_TEXT`表示僅限讀取文字。  
  
- `SF_RTF`指出讀取文字和格式。  
  
 這些值可以結合`SFF_SELECTION`。 如果`SFF_SELECTION`指定，則`StreamIn`取代目前的選取範圍的輸入資料流的內容。 如果未指定，`StreamIn`這整個內容取代`CRichEditCtrl`物件。  
  
 在**EDITSTREAM**參數`es`，指定填滿文字緩衝區的回呼函式。 此回呼函式稱為重複，直到已用完輸入資料流。  
  
 如需詳細資訊，請參閱[EM_STREAMIN](http://msdn.microsoft.com/library/windows/desktop/bb774302)訊息和[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&34;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_34.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&35;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_35.cpp)]  
  
##  <a name="streamout"></a>CRichEditCtrl::StreamOut  
 這個內容寫出`CRichEditCtrl`指定的輸出資料流的物件。  
  
```  
long StreamOut(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>參數  
 `nFormat`  
 旗標，指定輸出資料格式。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `es`  
 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)結構，指定輸出資料流。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="return-value"></a>傳回值  
 寫入輸出資料流的字元數。  
  
### <a name="remarks"></a>備註  
 值`nFormat`必須是下列其中之一︰  
  
- `SF_TEXT`表示只書寫文字。  
  
- `SF_RTF`表示寫入文字和格式。  
  
- `SF_RTFNOOBJS`表示書寫文字和格式設定，以空格取代 OLE 項目。  
  
- `SF_TEXTIZED`表示寫入文字和格式設定，以文字表示方式的 OLE 項目。  
  
 這些值可以結合`SFF_SELECTION`。 如果`SFF_SELECTION`指定，則`StreamOut`寫出到輸出資料流目前的選取範圍。 如果未指定，`StreamOut`寫出這樣的整個內容`CRichEditCtrl`物件。  
  
 在**EDITSTREAM**參數`es`，指定填滿文字緩衝區的回呼函式。 此回呼函式稱為重複，直到已用完的輸出資料流。  
  
 如需詳細資訊，請參閱[EM_STREAMOUT](http://msdn.microsoft.com/library/windows/desktop/bb774304)訊息和[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&36;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_36.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&37;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_37.cpp)]  
  
##  <a name="undo"></a>CRichEditCtrl::Undo  
 Rich edit 控制項中的最後一個作業復原。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>傳回值  
 如果復原作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 復原作業也會復原。 例如，您可以還原已刪除的文字，與第一次呼叫**復原**。 只要沒有任何中介的編輯作業，您可以移除第二次呼叫一次的文字**復原**。  
  
 如需詳細資訊，請參閱[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CanUndo](#canundo)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 WORDPAD](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CRichEditView 類別](../../mfc/reference/cricheditview-class.md)

