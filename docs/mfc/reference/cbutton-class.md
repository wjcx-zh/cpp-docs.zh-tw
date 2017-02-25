---
title: "CButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "button control [MFC]"
  - "button objects (CButton)"
  - "CButton class"
  - "核取方塊, button controls"
  - "checkbox buttons"
  - "pushbuttons"
  - "選項按鈕, CButton class"
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 按鈕控制項的功能。  
  
## 語法  
  
```  
class CButton : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CButton::CButton](../Topic/CButton::CButton.md)|建構 `CButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CButton::Create](../Topic/CButton::Create.md)|建立 Windows 按鈕控制項並將其附加至 `CButton` 物件。|  
|[CButton::DrawItem](../Topic/CButton::DrawItem.md)|繪製主控描繪 `CButton` 物件的覆寫。|  
|[CButton::GetBitmap](../Topic/CButton::GetBitmap.md)|擷取點陣圖的控制代碼之前設定與 [SetBitmap](../Topic/CButton::SetBitmap.md)。|  
|[CButton::GetButtonStyle](../Topic/CButton::GetButtonStyle.md)|擷取與按鈕控制項樣式的資訊。|  
|[CButton::GetCheck](../Topic/CButton::GetCheck.md)|擷取按鈕控制項的選取狀態。|  
|[CButton::GetCursor](../Topic/CButton::GetCursor.md)|擷取游標影像的控制代碼之前設定與 [SetCursor](../Topic/CButton::SetCursor.md)。|  
|[CButton::GetIcon](../Topic/CButton::GetIcon.md)|擷取圖示的控制代碼之前設定與 [SetIcon](../Topic/CButton::SetIcon.md)。|  
|[CButton::GetIdealSize](../Topic/CButton::GetIdealSize.md)|擷取按鈕控制項的理想的大小。|  
|[CButton::GetImageList](../Topic/CButton::GetImageList.md)|擷取按鈕控制項影像清單。|  
|[CButton::GetNote](../Topic/CButton::GetNote.md)|擷取目前命令連結控制元件的注意事項。|  
|[CButton::GetNoteLength](../Topic/CButton::GetNoteLength.md)|擷取附註文字長度目前命令連結控制項的。|  
|[CButton::GetSplitGlyph](../Topic/CButton::GetSplitGlyph.md)|擷取影像與目前分割按鈕控制項。|  
|[CButton::GetSplitImageList](../Topic/CButton::GetSplitImageList.md)|擷取目前分割按鈕控制項的影像清單。|  
|[CButton::GetSplitInfo](../Topic/CButton::GetSplitInfo.md)|擷取定義目前分割按鈕控制項的相關資訊。|  
|[CButton::GetSplitSize](../Topic/CButton::GetSplitSize.md)|擷取目前分割按鈕控制項的下拉式元件的週框 \(Bounding Rectangle\)。|  
|[CButton::GetSplitStyle](../Topic/CButton::GetSplitStyle.md)|擷取定義目前分割按鈕控制項的分割按鈕樣式。|  
|[CButton::GetState](../Topic/CButton::GetState.md)|擷取核取狀態、焦點狀態和按鈕控制項的焦點狀態。|  
|[CButton::GetTextMargin](../Topic/CButton::GetTextMargin.md)|擷取按鈕控制項的文字框線。|  
|[CButton::SetBitmap](../Topic/CButton::SetBitmap.md)|指定要在按鈕中顯示的點陣圖。|  
|[CButton::SetButtonStyle](../Topic/CButton::SetButtonStyle.md)|變更按鈕的樣式。|  
|[CButton::SetCheck](../Topic/CButton::SetCheck.md)|將按鈕控制項的選取狀態。|  
|[CButton::SetCursor](../Topic/CButton::SetCursor.md)|指定要在按鈕中顯示的游標影像。|  
|[CButton::SetDropDownState](../Topic/CButton::SetDropDownState.md)|設定目前分割按鈕控制項的下拉狀態。|  
|[CButton::SetIcon](../Topic/CButton::SetIcon.md)|指定要在按鈕中顯示的圖示。|  
|[CButton::SetImageList](../Topic/CButton::SetImageList.md)|將按鈕控制項影像清單。|  
|[CButton::SetNote](../Topic/CButton::SetNote.md)|設定有關目前命令連結控制的注意事項。|  
|[CButton::SetSplitGlyph](../Topic/CButton::SetSplitGlyph.md)|使指定的影像和目前分割按鈕控制項。|  
|[CButton::SetSplitImageList](../Topic/CButton::SetSplitImageList.md)|相關聯的影像清單與目前分割按鈕控制項。|  
|[CButton::SetSplitInfo](../Topic/CButton::SetSplitInfo.md)|指定定義目前分割按鈕控制項的相關資訊。|  
|[CButton::SetSplitSize](../Topic/CButton::SetSplitSize.md)|設定目前分割按鈕控制項的下拉式元件的週框 \(Bounding Rectangle\)。|  
|[CButton::SetSplitStyle](../Topic/CButton::SetSplitStyle.md)|設定目前分割按鈕控制項的樣式。|  
|[CButton::SetState](../Topic/CButton::SetState.md)|將按鈕控制項的反白顯示的狀態。|  
|[CButton::SetTextMargin](../Topic/CButton::SetTextMargin.md)|將按鈕控制項的文字框線。|  
  
## 備註  
 按鈕控制項是可以斷斷續續按一下的小矩形，子視窗。  按鈕單獨使用或在群組中，而可以標示或外觀，而不用文字。  當使用者按一下該按鈕時，通常會變更外觀。  
  
 一般按鈕為核取方塊、選項按鈕和按鈕。  `CButton` 物件可以根據 [按鈕樣式](../../mfc/reference/button-styles.md) 成為每一個，指定在其初始化由 [建立](../Topic/CButton::Create.md) 成員函式。  
  
 此外，從 `CButton` 衍生的 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) 類別支援按鈕控制項的建立標記的點陣圖影像 \(而非文字。  `CBitmapButton` 可以具有按鈕的，關閉，焦點和停用狀態的個別的點陣圖。  
  
 您可以建立一個按鈕控制項從對話方塊範本或直接在您的程式碼。  在這兩種情況下，請先呼叫建構 `CButton` 物件的 `CButton` ;然後呼叫 **建立** 成員函式建立 Windows 按鈕控制項並將它附加至 `CButton` 物件。  
  
 語法結構可以是從 `CButton`從衍生之類別中的程序。  提供衍生類別的建構函式和呼叫 **建立** 從建構函式中呼叫。  
  
 如果您想要處理 Windows 按鈕控制項傳送通知訊息至其父 [CDialog](../../mfc/reference/cdialog-class.md)\(通常是從衍生的類別\)，將訊息對應 \(Message Map 輸入和訊息處理常式成員函式來為每則訊息的父類別。  
  
 每個訊息對應 \(Message Map 輸入的格式如下:  
  
 **ON\_**告知**\(**`id`， `memberFxn`**\)**  
  
 其中 `id` 指定正在傳送之控制項的子視窗 ID 告知和 `memberFxn` 是您撰寫處理告知父代成員函式的名稱。  
  
 父的函式原型 \(Prototype\) 如下:  
  
 **afx\_msg** `void` `memberFxn` **\( \);**  
  
 可能的訊息對應 \(Message Map 輸入如下:  
  
|對應項目|傳送父代，當…|  
|----------|-------------|  
|**ON\_BN\_CLICKED**|使用者按一下  按鈕。|  
|**ON\_BN\_DOUBLECLICKED**|使用者按一下  按鈕。|  
  
 如果您從對話方塊資源的 `CButton` 物件，自動終結 `CButton` 物件，在使用者關閉對話方塊時。  
  
 如果您在視窗內的 `CButton` 物件，可能要終結它。  您可以使用 **new** 函式，建立。 `CButton` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結它，當使用者關閉 Windows 按鈕控制項時。  如果您在堆疊上建立 `CButton` 物件，或是在父對話方塊物件是內嵌，自動終結。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CBitmapButton Class](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)