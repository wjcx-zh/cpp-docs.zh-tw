---
title: "CEditView Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEditView class"
  - "edit controls, 類別"
  - "text editors"
  - "text editors, CEditView class"
  - "檢視, 類別"
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的檢視類別的型別所提供的 Windows 編輯控制項的功能，並且可以用來實作簡單的文字編輯器功能。  
  
## 語法  
  
```  
class CEditView : public CCtrlView  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CEditView::CEditView](../Topic/CEditView::CEditView.md)|建構物件型別 `CEditView`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CEditView::FindText](../Topic/CEditView::FindText.md)|搜尋文字中的字串。|  
|[CEditView::GetBufferLength](../Topic/CEditView::GetBufferLength.md)|取得字元緩衝區的長度。|  
|[CEditView::GetEditCtrl](../Topic/CEditView::GetEditCtrl.md)|提供對 `CEditView` 物件 \(Windows 編輯控制項\) 的 `CEdit` 部分。|  
|[CEditView::GetPrinterFont](../Topic/CEditView::GetPrinterFont.md)|擷取目前的印表機字型。|  
|[CEditView::GetSelectedText](../Topic/CEditView::GetSelectedText.md)|擷取目前文字選取範圍。|  
|[CEditView::LockBuffer](../Topic/CEditView::LockBuffer.md)|鎖定緩衝區。|  
|[CEditView::PrintInsideRect](../Topic/CEditView::PrintInsideRect.md)|呈現在指定矩形內的文字。|  
|[CEditView::SerializeRaw](../Topic/CEditView::SerializeRaw.md)|序列化至磁碟的物件 `CEditView` 做為原始文字。|  
|[CEditView::SetPrinterFont](../Topic/CEditView::SetPrinterFont.md)|會設定新的印表機字型。|  
|[CEditView::SetTabStops](../Topic/CEditView::SetTabStops.md)|將螢幕顯示和列印的定位停駐點。|  
|[CEditView::UnlockBuffer](../Topic/CEditView::UnlockBuffer.md)|開啟緩衝區。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CEditView::OnFindNext](../Topic/CEditView::OnFindNext.md)|文字字串中尋找下一個項目。|  
|[CEditView::OnReplaceAll](../Topic/CEditView::OnReplaceAll.md)|以新的字串取代成指定字串的所有項目。|  
|[CEditView::OnReplaceSel](../Topic/CEditView::OnReplaceSel.md)|取代目前的選取範圍。|  
|[CEditView::OnTextNotFound](../Topic/CEditView::OnTextNotFound.md)|呼叫，以尋找作業不會與任何其他文字。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CEditView::dwStyleDefault](../Topic/CEditView::dwStyleDefault.md)|型別 **CEditView.**物件的預設樣式。|  
  
## 備註  
 `CEditView` 類別提供下列各項:  
  
-   列印。  
  
-   尋找和取代。  
  
 因為類別是 `CEditView` 類別 `CView`衍生項目，類別 `CEditView` 物件可以與文件和文件樣板。  
  
 每個 `CEditView` 控制項文字在其全域記憶體物件保留。  您的應用程式可包含任何數目的 `CEditView` 物件。  
  
 請建立型別 `CEditView` 物件，如果您想要使用清單中所加入功能的編輯視窗上方，或者，如果您需要簡單的文字編輯器功能。  `CEditView` 物件可能會佔據視窗的整個工作區 \(Client Area\)。  從 `CEditView` 衍生您的類別中加入或修改的基礎功能，或宣告可以加入文件樣板的類別。  
  
 類別 `CEditView` 的預設實作會處理下列命令: **ID\_EDIT\_SELECT\_ALL**、 **ID\_EDIT\_FIND**、 **ID\_EDIT\_REPLACE**、 **ID\_EDIT\_REPEAT**和 **ID\_FILE\_PRINT**。  
  
 `CEditView` 的預設字元限制為 \(1024 \* 1024 \- 1 \= 1048575\)。  這可以呼叫基礎編輯控制項的 **EM\_LIMITTEXT** 函式變更。  不過，限制會根據作業系統和編輯控制項的型別不同 \(單一或多個資料列\)。  如需這些限制的詳細資訊，請參閱 [EM\_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)。  
  
 若要變更控制項的這個限制，請覆寫您的 `CEditView` 類別的 `OnCreate()` 函式並插入下列程式碼:  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/CPP/ceditview-class_1.cpp)]  
  
 型別 `CEditView` 物件 \(從 `CEditView`衍生類別或型別\) 具有下列限制:  
  
-   `CEditView` 不實作實際所見即所得的取得 \(WYSIWYG\) 編譯。  只要有在可讀性在螢幕和相對應的列印的輸出之間選擇， `CEditView` 選取螢幕可讀性。  
  
-   `CEditView` 只會顯示單一字型的文字。  特殊字元格式不受支援。  取得更大的功能參閱類別 [CRichEditView](../../mfc/reference/cricheditview-class.md) 。  
  
-   `CEditView` 可以包含的文字數會有所限制。  限制是相同的。 `CEdit` 控制項。  
  
 如需 `CEditView`的資訊，請參閱 [衍生的檢視類別適用於 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 SUPERPAD](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)