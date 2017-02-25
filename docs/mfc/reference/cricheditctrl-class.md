---
title: "CRichEditCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl class"
  - "CRichEditCtrl class, 通用控制項"
  - "formatted text [C++]"
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CRichEditCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Rich Edit 控制項的功能。  
  
## 語法  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditCtrl::CRichEditCtrl](../Topic/CRichEditCtrl::CRichEditCtrl.md)|建構 `CRichEditCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditCtrl::CanPaste](../Topic/CRichEditCtrl::CanPaste.md)|判斷剪貼簿的內容是否可貼到 Rich Edit 控制項。|  
|[CRichEditCtrl::CanRedo](../Topic/CRichEditCtrl::CanRedo.md)|判斷是否有在控制項取消復原佇列中的任何動作。|  
|[CRichEditCtrl::CanUndo](../Topic/CRichEditCtrl::CanUndo.md)|判斷編輯作業是否能夠復原。|  
|[CRichEditCtrl::CharFromPos](../Topic/CRichEditCtrl::CharFromPos.md)|擷取有關字元的資訊最接近在編輯控制項的工作區 \(Client Area\) 中指定的點。|  
|[CRichEditCtrl::Clear](../Topic/CRichEditCtrl::Clear.md)|清除目前選項。|  
|[CRichEditCtrl::Copy](../Topic/CRichEditCtrl::Copy.md)|複製目前的選取範圍複製到剪貼簿。|  
|[CRichEditCtrl::Create](../Topic/CRichEditCtrl::Create.md)|建立 Windows Rich Edit 控制項並將它與這個 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::CreateEx](../Topic/CRichEditCtrl::CreateEx.md)|建立具有指定的延伸視窗樣式的 Windows Rich Edit 控制項並將它與這個 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::Cut](../Topic/CRichEditCtrl::Cut.md)|剪下目前的選取範圍複製到剪貼簿。|  
|[CRichEditCtrl::DisplayBand](../Topic/CRichEditCtrl::DisplayBand.md)|顯示這個 `CRichEditCtrl` 物件內容的一部分。|  
|[CRichEditCtrl::EmptyUndoBuffer](../Topic/CRichEditCtrl::EmptyUndoBuffer.md)|會重設 \(清除\) 這個物件 `CRichEditCtrl` 復原旗標。|  
|[CRichEditCtrl::FindText](../Topic/CRichEditCtrl::FindText.md)|在這個 `CRichEditCtrl` 物件中的文字。|  
|[CRichEditCtrl::FindWordBreak](../Topic/CRichEditCtrl::FindWordBreak.md)|在指定的字元位置前後尋找下一個字中斷或擷取有關字元的資訊在該位置。|  
|[CRichEditCtrl::FormatRange](../Topic/CRichEditCtrl::FormatRange.md)|格式化文字的範圍目標輸出裝置的。|  
|[CRichEditCtrl::GetCharPos](../Topic/CRichEditCtrl::GetCharPos.md)|判斷指定的字元位置在這 `CRichEditCtrl` 物件內的。|  
|[CRichEditCtrl::GetDefaultCharFormat](../Topic/CRichEditCtrl::GetDefaultCharFormat.md)|擷取這 `CRichEditCtrl` 物件目前的預設字元格式的屬性。|  
|[CRichEditCtrl::GetEventMask](../Topic/CRichEditCtrl::GetEventMask.md)|擷取這個 `CRichEditCtrl` 物件的事件遮罩。|  
|[CRichEditCtrl::GetFirstVisibleLine](../Topic/CRichEditCtrl::GetFirstVisibleLine.md)|判斷在這個 `CRichEditCtrl` 物件的最頂端可見行。|  
|[CRichEditCtrl::GetIRichEditOle](../Topic/CRichEditCtrl::GetIRichEditOle.md)|擷取這個指標 Rich Edit 控制項的 `IRichEditOle` 介面。|  
|[CRichEditCtrl::GetLimitText](../Topic/CRichEditCtrl::GetLimitText.md)|取得使用者輸入至 `CRichEditCtrl` 物件的數量沒有限制文字。|  
|[CRichEditCtrl::GetLine](../Topic/CRichEditCtrl::GetLine.md)|從這個 `CRichEditCtrl` 物件擷取資料列的文字。|  
|[CRichEditCtrl::GetLineCount](../Topic/CRichEditCtrl::GetLineCount.md)|擷取行數。這 `CRichEditCtrl` 物件的。|  
|[CRichEditCtrl::GetModify](../Topic/CRichEditCtrl::GetModify.md)|判斷這個物件 `CRichEditCtrl` 內容是否已變更，因為最後一個儲存。|  
|[CRichEditCtrl::GetOptions](../Topic/CRichEditCtrl::GetOptions.md)|擷取 Rich Edit 控制項選項。|  
|[CRichEditCtrl::GetParaFormat](../Topic/CRichEditCtrl::GetParaFormat.md)|擷取目前選取的段落格式屬性在這個 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::GetPunctuation](../Topic/CRichEditCtrl::GetPunctuation.md)|擷取 Rich Edit 控制項的目前標點符號。  這個訊息只具有作業系統之亞洲語言版本。|  
|[CRichEditCtrl::GetRect](../Topic/CRichEditCtrl::GetRect.md)|擷取這個物件的 `CRichEditCtrl` 格式化矩形。|  
|[CRichEditCtrl::GetRedoName](../Topic/CRichEditCtrl::GetRedoName.md)|擷取下一個動作類型，如果有的話，在控制項取消復原佇列。|  
|[CRichEditCtrl::GetSel](../Topic/CRichEditCtrl::GetSel.md)|取得目前選取範圍的開始和結尾位置。這 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::GetSelectionCharFormat](../Topic/CRichEditCtrl::GetSelectionCharFormat.md)|擷取目前選取範圍中的字元格式屬性在這個 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::GetSelectionType](../Topic/CRichEditCtrl::GetSelectionType.md)|要擷取內容的型別會在目前選取範圍中的 \[ `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::GetSelText](../Topic/CRichEditCtrl::GetSelText.md)|取得目前選取的文字在這個物件的 `CRichEditCtrl`|  
|[CRichEditCtrl::GetTextLength](../Topic/CRichEditCtrl::GetTextLength.md)|擷取文字的長度，以字元為單位\)，在此 `CRichEditCtrl` 物件。  包括結束的 null 字元。|  
|[CRichEditCtrl::GetTextLengthEx](../Topic/CRichEditCtrl::GetTextLengthEx.md)|擷取字元或位元組數目豐富的編輯檢視。  接受旗標清單指出判斷文字長度方法在 Rich Edit 控制項|  
|[CRichEditCtrl::GetTextMode](../Topic/CRichEditCtrl::GetTextMode.md)|擷取 Rich Edit 控制項的目前文字模式和復原層級。|  
|[CRichEditCtrl::GetTextRange](../Topic/CRichEditCtrl::GetTextRange.md)|擷取指定的文字範圍。|  
|[CRichEditCtrl::GetUndoName](../Topic/CRichEditCtrl::GetUndoName.md)|擷取下一個復原動作類型，如果有的話，一次。|  
|[CRichEditCtrl::GetWordWrapMode](../Topic/CRichEditCtrl::GetWordWrapMode.md)|擷取包裝目前中斷 Rich Edit 控制項的文字和文字選項。  這個訊息只具有作業系統之亞洲語言版本。|  
|[CRichEditCtrl::HideSelection](../Topic/CRichEditCtrl::HideSelection.md)|顯示或隱藏目前的選取範圍。|  
|[CRichEditCtrl::LimitText](../Topic/CRichEditCtrl::LimitText.md)|限制使用者可輸入 `CRichEditCtrl` 物件中的文字數。|  
|[CRichEditCtrl::LineFromChar](../Topic/CRichEditCtrl::LineFromChar.md)|判斷哪一行包含指定字元。|  
|[CRichEditCtrl::LineIndex](../Topic/CRichEditCtrl::LineIndex.md)|擷取指定行字元索引執行 `CRichEditCtrl` 物件的。|  
|[CRichEditCtrl::LineLength](../Topic/CRichEditCtrl::LineLength.md)|擷取指定行長度在這 `CRichEditCtrl` 物件的。|  
|[CRichEditCtrl::LineScroll](../Topic/CRichEditCtrl::LineScroll.md)|在此清單中 `CRichEditCtrl` 物件的文字。|  
|[CRichEditCtrl::Paste](../Topic/CRichEditCtrl::Paste.md)|將剪貼簿的內容貼至這 Rich Edit 控制項。|  
|[CRichEditCtrl::PasteSpecial](../Topic/CRichEditCtrl::PasteSpecial.md)|將剪貼簿的內容貼至指定的資料格式中的這個 Rich Edit 控制項。|  
|[CRichEditCtrl::PosFromChar](../Topic/CRichEditCtrl::PosFromChar.md)|擷取指定之字元的工作區座標 \(以編輯控制項的。|  
|[CRichEditCtrl::Redo](../Topic/CRichEditCtrl::Redo.md)|取消復原控制項取消復原佇列中的下一個動作。|  
|[CRichEditCtrl::ReplaceSel](../Topic/CRichEditCtrl::ReplaceSel.md)|使用指定的文字取代此 `CRichEditCtrl` 物件目前的選取範圍。|  
|[CRichEditCtrl::RequestResize](../Topic/CRichEditCtrl::RequestResize.md)|強制此 `CRichEditCtrl` 物件傳送要求調整告知。|  
|[CRichEditCtrl::SetAutoURLDetect](../Topic/CRichEditCtrl::SetAutoURLDetect.md)|表示要自動偵測 URL 是否為作用中的 Rich Edit 控制項。|  
|[CRichEditCtrl::SetBackgroundColor](../Topic/CRichEditCtrl::SetBackgroundColor.md)|設定這個 `CRichEditCtrl` 物件的背景色彩。|  
|[CRichEditCtrl::SetDefaultCharFormat](../Topic/CRichEditCtrl::SetDefaultCharFormat.md)|設定這個 `CRichEditCtrl` 物件目前的預設字元格式的屬性。|  
|[CRichEditCtrl::SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md)|設定這 `CRichEditCtrl` 物件的事件遮罩。|  
|[CRichEditCtrl::SetModify](../Topic/CRichEditCtrl::SetModify.md)|設定或清除這個 `CRichEditCtrl` 物件的修改旗標。|  
|[CRichEditCtrl::SetOLECallback](../Topic/CRichEditCtrl::SetOLECallback.md)|設定這個 Rich Edit 控制項的 `IRichEditOleCallback` COM 物件。|  
|[CRichEditCtrl::SetOptions](../Topic/CRichEditCtrl::SetOptions.md)|設定這 `CRichEditCtrl` 物件的選項。|  
|[CRichEditCtrl::SetParaFormat](../Topic/CRichEditCtrl::SetParaFormat.md)|設定目前選取的段落格式屬性在這個 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::SetPunctuation](../Topic/CRichEditCtrl::SetPunctuation.md)|設定 Rich Edit 控制項的標點符號。  這個訊息只具有作業系統之亞洲語言版本。|  
|[CRichEditCtrl::SetReadOnly](../Topic/CRichEditCtrl::SetReadOnly.md)|設定這 `CRichEditCtrl` 物件的唯讀選項。|  
|[CRichEditCtrl::SetRect](../Topic/CRichEditCtrl::SetRect.md)|設定這 `CRichEditCtrl` 物件的格式化矩形。|  
|[CRichEditCtrl::SetSel](../Topic/CRichEditCtrl::SetSel.md)|設定這個 `CRichEditCtrl` 物件的選取範圍。|  
|[CRichEditCtrl::SetSelectionCharFormat](../Topic/CRichEditCtrl::SetSelectionCharFormat.md)|設定目前選取範圍中的字元格式屬性在這個 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::SetTargetDevice](../Topic/CRichEditCtrl::SetTargetDevice.md)|設定這 `CRichEditCtrl` 物件的目標輸出裝置的方法。|  
|[CRichEditCtrl::SetTextMode](../Topic/CRichEditCtrl::SetTextMode.md)|設定 Rich Edit 控制項的文字模式或復原層級。  如果控制項包含文字，訊息會失敗。|  
|[CRichEditCtrl::SetUndoLimit](../Topic/CRichEditCtrl::SetUndoLimit.md)|設定復原佇列中儲存的動作數目上限。|  
|[CRichEditCtrl::SetWordCharFormat](../Topic/CRichEditCtrl::SetWordCharFormat.md)|將目前的文字字元格式的屬性是在此 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::SetWordWrapMode](../Topic/CRichEditCtrl::SetWordWrapMode.md)|設定自動換行和 Rich Edit 控制項的文字中斷選項。  這個訊息只具有作業系統之亞洲語言版本。|  
|[CRichEditCtrl::StopGroupTyping](../Topic/CRichEditCtrl::StopGroupTyping.md)|從收集其他輸入的動作停止控制項到目前的復原動作。  控制項會儲存一次輸入的動作，如果有的話，來復原佇列的新的動作的。|  
|[CRichEditCtrl::StreamIn](../Topic/CRichEditCtrl::StreamIn.md)|不會將輸入資料流文字至 `CRichEditCtrl` 物件。|  
|[CRichEditCtrl::StreamOut](../Topic/CRichEditCtrl::StreamOut.md)|儲存從這個物件 `CRichEditCtrl` 文字至輸出資料流。|  
|[CRichEditCtrl::Undo](../Topic/CRichEditCtrl::Undo.md)|反轉最後編輯作業。|  
  
## 備註  
 「Rich Edit 控制項」是使用者可以輸入和編輯文字的視窗。  文字指派字元和段落格式，並且可以包含內嵌的 OLE 物件。  Rich Edit 控制項提供格式化文字提供程式設計介面。  然而，應用程式必須實作所有必要使用者介面的元件已格式化作業給使用者使用。  
  
 這個 Windows 通用控制項 \(也 `CRichEditCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  `CRichEditCtrl` 類別支援 2.0 版和 3.0 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] Rich Edit 控制項。  
  
> [!CAUTION]
>  如果您在  對話方塊中使用 Rich Edit 控制項 \(不論應用程式是 SDI、MDI，對話方塊架構\)，您必須呼叫一次 [AfxInitRichEdit](../Topic/AfxInitRichEdit.md) ，在  對話方塊隨即顯示。  呼叫這個函式的一般位置的程式 `InitInstance` 的成員函式。  您不需要呼叫它，每一次顯示  對話方塊中，只會在第一次的。  如果您使用， `CRichEditView`一起使用，並不需要呼叫 `AfxInitRichEdit` 。  
  
 如需使用 `CRichEditCtrl`的資訊，請參閱:  
  
-   [控制項](../../mfc/controls-mfc.md)  
  
-   [使用 CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   知識庫文件 Q259949:詳細資訊:SetCaretPos \(\) 不是適當的使用 CEdit 或 CRichEditCtrl 控制項  
  
 如需使用範例 Rich Edit 控制項在 MFC 應用程式，請參閱 [WORDPAD](../../top/visual-cpp-samples.md) 範例應用程式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 WORDPAD](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)