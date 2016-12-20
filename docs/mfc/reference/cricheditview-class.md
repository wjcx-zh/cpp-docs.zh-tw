---
title: "CRichEditView Class | Microsoft Docs"
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
  - "CRichEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditView class"
  - "document/view architecture, Rich Edit 控制項"
  - "OLE containers, rich edit"
  - "Rich Edit 控制項, OLE container"
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRichEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) 和 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)， MFC 中的文件檢視架構內容中提供 Rich Edit 控制項的功能。  
  
## 語法  
  
```  
  
class CRichEditView : public CCtrlView  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditView::CRichEditView](../Topic/CRichEditView::CRichEditView.md)|建構 `CRichEditView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditView::AdjustDialogPosition](../Topic/CRichEditView::AdjustDialogPosition.md)|將對話方塊，使其不會遮蔽到目前的選取範圍。|  
|[CRichEditView::CanPaste](../Topic/CRichEditView::CanPaste.md)|告知剪貼簿是否包含可貼入 Rich Edit 檢視中的資料。|  
|[CRichEditView::DoPaste](../Topic/CRichEditView::DoPaste.md)|貼上的 OLE 項目至豐富的編輯檢視。|  
|[CRichEditView::FindText](../Topic/CRichEditView::FindText.md)|找到指定的文字，叫用等待游標。|  
|[CRichEditView::FindTextSimple](../Topic/CRichEditView::FindTextSimple.md)|找到指定的文字。|  
|[CRichEditView::GetCharFormatSelection](../Topic/CRichEditView::GetCharFormatSelection.md)|擷取目前選取範圍的字元格式的屬性。|  
|[CRichEditView::GetDocument](../Topic/CRichEditView::GetDocument.md)|擷取指標相關 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|  
|[CRichEditView::GetInPlaceActiveItem](../Topic/CRichEditView::GetInPlaceActiveItem.md)|擷取目前在豐富的編輯檢視的就地啟動的 OLE 項目。|  
|[CRichEditView::GetMargins](../Topic/CRichEditView::GetMargins.md)|擷取這個豐富的編輯檢視的框線。|  
|[CRichEditView::GetPageRect](../Topic/CRichEditView::GetPageRect.md)|擷取這個豐富的編輯檢視網頁的矩形。|  
|[CRichEditView::GetPaperSize](../Topic/CRichEditView::GetPaperSize.md)|擷取這個豐富的編輯檢視的紙張大小。|  
|[CRichEditView::GetParaFormatSelection](../Topic/CRichEditView::GetParaFormatSelection.md)|擷取目前選取的段落格式屬性。|  
|[CRichEditView::GetPrintRect](../Topic/CRichEditView::GetPrintRect.md)|擷取這個豐富的編輯檢視的列印矩形。|  
|[CRichEditView::GetPrintWidth](../Topic/CRichEditView::GetPrintWidth.md)|擷取這個豐富的編輯檢視的列印寬度。|  
|[CRichEditView::GetRichEditCtrl](../Topic/CRichEditView::GetRichEditCtrl.md)|擷取 Rich Edit 控制項。|  
|[CRichEditView::GetSelectedItem](../Topic/CRichEditView::GetSelectedItem.md)|從豐富的編輯檢視擷取選取的項目。|  
|[CRichEditView::GetTextLength](../Topic/CRichEditView::GetTextLength.md)|擷取文字的長度 \(以豐富的編輯檢視。|  
|[CRichEditView::GetTextLengthEx](../Topic/CRichEditView::GetTextLengthEx.md)|擷取字元或位元組數目豐富的編輯檢視。  判斷長度方法的展開旗標清單。|  
|[CRichEditView::InsertFileAsObject](../Topic/CRichEditView::InsertFileAsObject.md)|外掛程式檔案當做 OLE 項目。|  
|[CRichEditView::InsertItem](../Topic/CRichEditView::InsertItem.md)|插入新項目當做 OLE 項目。|  
|[CRichEditView::IsRichEditFormat](../Topic/CRichEditView::IsRichEditFormat.md)|告知剪貼簿是否具有豐富的編輯或文字格式包含資料。|  
|[CRichEditView::OnCharEffect](../Topic/CRichEditView::OnCharEffect.md)|切換目前選取範圍的字元格式。|  
|[CRichEditView::OnParaAlign](../Topic/CRichEditView::OnParaAlign.md)|變更區段的對齊方式。|  
|[CRichEditView::OnUpdateCharEffect](../Topic/CRichEditView::OnUpdateCharEffect.md)|更新字元公用成員函式的命令 UI。|  
|[CRichEditView::OnUpdateParaAlign](../Topic/CRichEditView::OnUpdateParaAlign.md)|更新的 Public 成員函式的命令 UI。|  
|[CRichEditView::PrintInsideRect](../Topic/CRichEditView::PrintInsideRect.md)|格式化在指定矩形內所指定文字。|  
|[CRichEditView::PrintPage](../Topic/CRichEditView::PrintPage.md)|格式化在特定頁面中指定的文字。|  
|[CRichEditView::SetCharFormat](../Topic/CRichEditView::SetCharFormat.md)|設定目前選取範圍的字元格式的屬性。|  
|[CRichEditView::SetMargins](../Topic/CRichEditView::SetMargins.md)|設定這個豐富的編輯檢視的框線。|  
|[CRichEditView::SetPaperSize](../Topic/CRichEditView::SetPaperSize.md)|設定這個豐富的編輯檢視的紙張大小。|  
|[CRichEditView::SetParaFormat](../Topic/CRichEditView::SetParaFormat.md)|設定目前選取的段落格式屬性。|  
|[CRichEditView::TextNotFound](../Topic/CRichEditView::TextNotFound.md)|將控制項的內部查閱狀態。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditView::GetClipboardData](../Topic/CRichEditView::GetClipboardData.md)|擷取一個範圍的剪貼簿物件包含豐富的編輯檢視。|  
|[CRichEditView::GetContextMenu](../Topic/CRichEditView::GetContextMenu.md)|以滑鼠右鍵按鈕擷取內容功能表使用向下。|  
|[CRichEditView::IsSelected](../Topic/CRichEditView::IsSelected.md)|指出指定的 OLE 項目是否已選取。|  
|[CRichEditView::OnFindNext](../Topic/CRichEditView::OnFindNext.md)|尋找子字串的下一個出現位置。|  
|[CRichEditView::OnInitialUpdate](../Topic/CRichEditView::OnInitialUpdate.md)|在第一次附加至文件時，重新整理檢視。|  
|[CRichEditView::OnPasteNativeObject](../Topic/CRichEditView::OnPasteNativeObject.md)|從 OLE 項目擷取原生資料。|  
|[CRichEditView::OnPrinterChanged](../Topic/CRichEditView::OnPrinterChanged.md)|設定列印特性指派給特定裝置。|  
|[CRichEditView::OnReplaceAll](../Topic/CRichEditView::OnReplaceAll.md)|以新的字串取代成指定字串的所有項目。|  
|[CRichEditView::OnReplaceSel](../Topic/CRichEditView::OnReplaceSel.md)|取代目前的選取範圍。|  
|[CRichEditView::OnTextNotFound](../Topic/CRichEditView::OnTextNotFound.md)|處理使用者告知找不到要求的文字。|  
|[CRichEditView::QueryAcceptData](../Topic/CRichEditView::QueryAcceptData.md)|請參閱的查詢。如需 `IDataObject`的資料。|  
|[CRichEditView::WrapChanged](../Topic/CRichEditView::WrapChanged.md)|對於這個豐富的編輯檢視調整目標輸出裝置，根據 `m_nWordWrap`的值。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRichEditView::m\_nBulletIndent](../Topic/CRichEditView::m_nBulletIndent.md)|表示量項目符號清單的縮排。|  
|[CRichEditView::m\_nWordWrap](../Topic/CRichEditView::m_nWordWrap.md)|表示自動換行條件約束。|  
  
## 備註  
 「Rich Edit 控制項」是使用者可以輸入和編輯文字的視窗。  文字指派字元和段落格式，並且可以包含內嵌的 OLE 物件。  Rich Edit 控制項提供格式化文字提供程式設計介面。  然而，應用程式必須實作所有必要使用者介面的元件已格式化作業給使用者使用。  
  
 `CRichEditView` 維持文字和格式一般文字。  `CRichEditDoc` 維護這個檢視 OLE 用戶端項目的清單。  `CRichEditCntrItem` 提供容器的存取 OLE 用戶端項目。  
  
 這個 Windows 通用控制項 \(也 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相關類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用範例的豐富的編輯檢視在 MFC 應用程式，請參閱 [WORDPAD](../../top/visual-cpp-samples.md) 範例應用程式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## 需求  
 **Header:** afxrich.h  
  
## 請參閱  
 [MFC 範例 WORDPAD](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem Class](../../mfc/reference/cricheditcntritem-class.md)