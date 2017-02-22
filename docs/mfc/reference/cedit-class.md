---
title: "CEdit Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEdit class"
  - "控制項 [MFC], edit"
  - "edit controls"
  - "edit controls, 類別"
  - "line separators in multiline edit controls"
  - "multiline edit control"
  - "分隔符號, in multiline edit controls"
  - "text editors"
  - "text editors, CEdit class"
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 編輯控制項的功能。  
  
## 語法  
  
```  
class CEdit : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CEdit::CEdit](../Topic/CEdit::CEdit.md)|建構 `CEdit` 控制項物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CEdit::CanUndo](../Topic/CEdit::CanUndo.md)|判斷控制項是否能夠復原作業。|  
|[CEdit::CharFromPos](../Topic/CEdit::CharFromPos.md)|擷取字元的行和字元索引最接近的指定位置。|  
|[CEdit::Clear](../Topic/CEdit::Clear.md)|刪除 \(\) 清除目前的選取範圍 \(如果有的話\) 在編輯控制項。|  
|[CEdit::Copy](../Topic/CEdit::Copy.md)|複製目前的選取範圍 \(如果有的話\) 在編輯控制項加入至 **CF\_TEXT** 格式的剪貼簿。|  
|[CEdit::Create](../Topic/CEdit::Create.md)|建立 Windows 編輯控制項並將其附加至 `CEdit` 物件。|  
|[CEdit::Cut](../Topic/CEdit::Cut.md)|刪除 \(\) 剪下目前的選取範圍 \(如果有的話\) 在編輯控制項和複製刪除的文字加入至 **CF\_TEXT** 格式的剪貼簿。|  
|[CEdit::EmptyUndoBuffer](../Topic/CEdit::EmptyUndoBuffer.md)|會重設 \(清除\) 編輯控制項的復原旗標。|  
|[CEdit::FmtLines](../Topic/CEdit::FmtLines.md)|設定軟體的分行符號字元包括開啟或關閉在多行編輯控制項中。|  
|[CEdit::GetCueBanner](../Topic/CEdit::GetCueBanner.md)|擷取顯示為文字提示的文字，或提示，以編輯控制項，當控制項是空的，但沒有焦點時。|  
|[CEdit::GetFirstVisibleLine](../Topic/CEdit::GetFirstVisibleLine.md)|判斷編輯控制項的最頂端可見行。|  
|[CEdit::GetHandle](../Topic/CEdit::GetHandle.md)|擷取控制代碼為多行編輯控制項中目前已配置的記憶體。|  
|[CEdit::GetHighlight](../Topic/CEdit::GetHighlight.md)|取得開始和結束字元的索引是在目前的編輯控制項中反白顯示文字的範圍。|  
|[CEdit::GetLimitText](../Topic/CEdit::GetLimitText.md)|取得這個 `CEdit` 可以包含的最大記憶體量文字。|  
|[CEdit::GetLine](../Topic/CEdit::GetLine.md)|從編輯控制項擷取資料列的文字。|  
|[CEdit::GetLineCount](../Topic/CEdit::GetLineCount.md)|擷取行數多行編輯控制項的。|  
|[CEdit::GetMargins](../Topic/CEdit::GetMargins.md)|取得這個 `CEdit`的左框線。|  
|[CEdit::GetModify](../Topic/CEdit::GetModify.md)|判斷是否已修改編輯控制項的內容。|  
|[CEdit::GetPasswordChar](../Topic/CEdit::GetPasswordChar.md)|當使用者輸入文字時，會擷取在編輯控制項中顯示的密碼字元。|  
|[CEdit::GetRect](../Topic/CEdit::GetRect.md)|取得編輯控制項的格式化矩形。|  
|[CEdit::GetSel](../Topic/CEdit::GetSel.md)|取得目前選取範圍中的第一個和最後一個字元位置在編輯控制項。|  
|[CEdit::HideBalloonTip](../Topic/CEdit::HideBalloonTip.md)|隱藏所有汽球提示與目前編輯控制項。|  
|[CEdit::LimitText](../Topic/CEdit::LimitText.md)|限制使用者可輸入 Edit 控制項文字的長度。|  
|[CEdit::LineFromChar](../Topic/CEdit::LineFromChar.md)|擷取包含指定字元索引之行的行號。|  
|[CEdit::LineIndex](../Topic/CEdit::LineIndex.md)|擷取一行的字元索引多行編輯控制項中。|  
|[CEdit::LineLength](../Topic/CEdit::LineLength.md)|擷取一行的長度 \(以編輯控制項的。|  
|[CEdit::LineScroll](../Topic/CEdit::LineScroll.md)|移動多行編輯控制項的文字。|  
|[CEdit::Paste](../Topic/CEdit::Paste.md)|貼上剪貼簿中的資料至編輯控制項會在目前游標位置。  資料，只有在剪貼簿中 **CF\_TEXT** 格式，其中包含的資料插入。|  
|[CEdit::PosFromChar](../Topic/CEdit::PosFromChar.md)|擷取指定之字元索引的左上角座標。|  
|[CEdit::ReplaceSel](../Topic/CEdit::ReplaceSel.md)|使用指定的文字取代編輯控制項的目前選取範圍。|  
|[CEdit::SetCueBanner](../Topic/CEdit::SetCueBanner.md)|設定顯示為文字提示的文字，或提示，以編輯控制項，當控制項是空的，但沒有焦點時。|  
|[CEdit::SetHandle](../Topic/CEdit::SetHandle.md)|將控制代碼是要供多行編輯控制項所使用的本機記憶體。|  
|[CEdit::SetHighlight](../Topic/CEdit::SetHighlight.md)|反白顯示在目前編輯控制項中顯示之文字的範圍。|  
|[CEdit::SetLimitText](../Topic/CEdit::SetLimitText.md)|設定這 `CEdit` 可以包含的最大記憶體量文字。|  
|[CEdit::SetMargins](../Topic/CEdit::SetMargins.md)|設定這 `CEdit`的左框線。|  
|[CEdit::SetModify](../Topic/CEdit::SetModify.md)|設定或清除編輯控制項修改旗標。|  
|[CEdit::SetPasswordChar](../Topic/CEdit::SetPasswordChar.md)|當使用者輸入文字時，設定或移除在編輯控制項中顯示的密碼字元。|  
|[CEdit::SetReadOnly](../Topic/CEdit::SetReadOnly.md)|將編輯控制項的唯讀狀態。|  
|[CEdit::SetRect](../Topic/CEdit::SetRect.md)|設定多行編輯控制項的格式化矩形並更新控制項。|  
|[CEdit::SetRectNP](../Topic/CEdit::SetRectNP.md)|設定多行編輯控制項的格式化矩形，而不用重新繪製控制項的視窗。|  
|[CEdit::SetSel](../Topic/CEdit::SetSel.md)|選取某個字元範圍在編輯控制項的。|  
|[CEdit::SetTabStops](../Topic/CEdit::SetTabStops.md)|設定在多行編輯控制項的定位停駐點。|  
|[CEdit::ShowBalloonTip](../Topic/CEdit::ShowBalloonTip.md)|顯示與目前編輯控制項中顯示汽球提示。|  
|[CEdit::Undo](../Topic/CEdit::Undo.md)|反轉最後一項作業。|  
  
## 備註  
 編輯控制項是使用者可以輸入文字的矩形子視窗。  
  
 您可以建立一個編輯控制項從對話方塊範本或直接在您的程式碼。  在這兩種情況下，請先呼叫建構函式 `CEdit` 建構物件，然後呼叫 [建立](../Topic/CEdit::Create.md) 成員函式建立 Windows 編輯控制項並將它附加至的 `CEdit``CEdit` 物件。  
  
 語法結構可以是從 `CEdit`從衍生之類別中的程序。  提供衍生類別的建構函式和呼叫 **建立** 從建構函式中呼叫。  
  
 `CEdit` 繼承自 `CWnd`的重要功能。  從 `CEdit` 物件要設定和擷取文字，請使用 `CWnd` 成員函式 [SetWindowText](../Topic/CWnd::SetWindowText.md) 和 [GetWindowText](../Topic/CWnd::GetWindowText.md)，設定或取得編輯控制項的整個內容，，即使它是多行控制項。  在多行控制項中的文字行是「\\ r \\ n 一連串字元分隔。  此外，如果，編輯控制項是多行， get 和控制項的文字區段集合藉由呼叫 `CEdit` 成員函式 [GetLine](../Topic/CEdit::GetLine.md)， [SetSel](../Topic/CEdit::SetSel.md)、 [GetSel](../Topic/CEdit::GetSel.md)和 [ReplaceSel](../Topic/CEdit::ReplaceSel.md)。  
  
 如果您要處理的 Windows 編輯控制項所傳送的通知訊息給它的父 `CDialog`\(通常是從衍生的類別\)，將訊息對應 \(Message Map 輸入和訊息處理常式成員函式來為每則訊息的父類別。  
  
 每個訊息對應 \(Message Map 輸入的格式如下:  
  
 **ON\_**告知**\(***ID， memberFxn***\)**  
  
 其中 `id` 指定傳送的編輯控制項的子視窗 ID 告知和 `memberFxn` 是您撰寫處理告知父代成員函式的名稱。  
  
 父的函式原型 \(Prototype\) 如下:  
  
 **afx\_msg** void memberFxn**\( \);**  
  
 下列可能的訊息對應項目並將它們傳送至父控制項描述清單:  
  
-   **ON\_EN\_CHANGE** 使用者採取可能已修改中編輯控制項的文字的動作。  不同於 **EN\_UPDATE** 通知訊息，在這種情況下，視窗都會更新以顯示之後，這就會傳送通知訊息。  
  
-   **ON\_EN\_ERRSPACE** 編輯控制項無法配置足夠的記憶體以符合特定需求。  
  
-   **ON\_EN\_HSCROLL** 使用者按一下編輯控制項的水平捲軸。  以螢幕更新之前，父視窗時收到通知。  
  
-   **ON\_EN\_KILLFOCUS** 編輯控制項失去輸入焦點。  
  
-   **ON\_EN\_MAXTEXT** 目前插入超過指定字元數的編輯控制項的和會被截斷。  也可以傳送時，編輯控制項時不 **ES\_AUTOHSCROLL** 樣式和要插入的字元數超過編輯控制項的寬度。  也可以傳送時，編輯控制項時不 **ES\_AUTOVSCROLL** 樣式和總數。由於會超出插入文字編輯控制項的高度。  
  
-   在編輯控制項收到輸入焦點時，**ON\_EN\_SETFOCUS** 傳送。  
  
-   **ON\_EN\_UPDATE** 編輯控制項會顯示修改後的文字。  傳送，在控制項已格式化文字之後，但在，它會篩選文字之前，讓視窗大小可以進行修改，如果需要。  
  
-   **ON\_EN\_VSCROLL** 使用者按一下編輯控制項的垂直捲軸。  以螢幕更新之前，父視窗時收到通知。  
  
 如果您在對話方塊內的 `CEdit` 物件，自動終結 `CEdit` 物件，在使用者關閉對話方塊時。  
  
 使用對話方塊編輯器中，如果您從對話方塊資源的 `CEdit` 物件，自動終結 `CEdit` 物件，在使用者關閉對話方塊時。  
  
 如果您在視窗內的 `CEdit` 物件，可能還需要終結它。  如果您在堆疊上建立物件， `CEdit` 自動終結。  您可以使用 **new** 函式，建立。 `CEdit` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結此物件，在使用者結束的 Windows 編輯控制項時。  如果您在 `CEdit` 配置物件的任何記憶體，請覆寫 `CEdit` 解構函式處理組態。  
  
 若要修改在編輯控制項的特定模式 \(例如 **ES\_READONLY**\) 必須傳送特定資訊加入至控制項而不是使用 [ModifyStyle](../Topic/CWnd::ModifyStyle.md)。  請參閱在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [編輯控制項模式](http://msdn.microsoft.com/library/windows/desktop/bb775464) 。  
  
 如需 `CEdit`的資訊，請參閱:  
  
-   [控制項](../../mfc/controls-mfc.md)  
  
-   知識庫文件 Q259949:詳細資訊:SetCaretPos \(\) 不是適當的使用 CEdit 或 CRichEditCtrl 控制項  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CEdit`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 CALCDRIV](../../top/visual-cpp-samples.md)   
 [MFC 範例 CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)