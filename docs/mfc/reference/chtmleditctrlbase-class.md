---
title: "CHtmlEditCtrlBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHtmlEditCtrlBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditCtrlBase class"
ms.assetid: e0cc74b4-8320-4570-b673-16c03d2ae266
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHtmlEditCtrlBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示編輯元件的 HTML。  
  
## 語法  
  
```  
  
template < class   
T  
 > class CHtmlEditCtrlBase  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHtmlEditCtrlBase::AddToGlyphTable](../Topic/CHtmlEditCtrlBase::AddToGlyphTable.md)|將項目加入至影像資料表，在設計模式中控制項的特定標記顯示。|  
|[CHtmlEditCtrlBase::Bold](../Topic/CHtmlEditCtrlBase::Bold.md)|切換選取之文字的粗體狀態。|  
|[CHtmlEditCtrlBase::Button](../Topic/CHtmlEditCtrlBase::Button.md)|覆寫目前選取範圍上建立按鈕控制項。|  
|[CHtmlEditCtrlBase::CheckBox](../Topic/CHtmlEditCtrlBase::CheckBox.md)|覆寫目前選取的核取方塊控制項。|  
|[CHtmlEditCtrlBase::ClearSelection](../Topic/CHtmlEditCtrlBase::ClearSelection.md)|清除目前選項。|  
|[CHtmlEditCtrlBase::Copy](../Topic/CHtmlEditCtrlBase::Copy.md)|複製目前的選取範圍複製到剪貼簿。|  
|[CHtmlEditCtrlBase::Cut](../Topic/CHtmlEditCtrlBase::Cut.md)|複製目前的選取範圍複製到剪貼簿並加以刪除。|  
|[CHtmlEditCtrlBase::Delete](../Topic/CHtmlEditCtrlBase::Delete.md)|刪除目前的選取範圍。|  
|[CHtmlEditCtrlBase::DropDownBox](../Topic/CHtmlEditCtrlBase::DropDownBox.md)|覆寫目前選取範圍的下拉式清單選取控制項。|  
|[CHtmlEditCtrlBase::EmptyGlyphTable](../Topic/CHtmlEditCtrlBase::EmptyGlyphTable.md)|從影像資料表移除所有項目，在設計模式中隱藏對標籤顯示的所有影像。|  
|[CHtmlEditCtrlBase::ExecCommand](../Topic/CHtmlEditCtrlBase::ExecCommand.md)|執行命令。|  
|[CHtmlEditCtrlBase::Font](../Topic/CHtmlEditCtrlBase::Font.md)|開啟 \[字型\] 對話方塊可讓使用者變更目前選取項目的文字色彩、字型和字型大小。|  
|[CHtmlEditCtrlBase::GetAbsolutePosition](../Topic/CHtmlEditCtrlBase::GetAbsolutePosition.md)|傳回項目的位置屬性是否為「Absolute」。|  
|[CHtmlEditCtrlBase::GetBackColor](../Topic/CHtmlEditCtrlBase::GetBackColor.md)|擷取目前選取項目的背景色彩。|  
|[CHtmlEditCtrlBase::GetBlockFormat](../Topic/CHtmlEditCtrlBase::GetBlockFormat.md)|擷取目前的格式標記。|  
|[CHtmlEditCtrlBase::GetBlockFormatNames](../Topic/CHtmlEditCtrlBase::GetBlockFormatNames.md)|擷取字串與可用格式的標記對應。|  
|[CHtmlEditCtrlBase::GetBookMark](../Topic/CHtmlEditCtrlBase::GetBookMark.md)|擷取書籤錨定的名稱。|  
|[CHtmlEditCtrlBase::GetDocument](../Topic/CHtmlEditCtrlBase::GetDocument.md)|擷取文件物件。|  
|[CHtmlEditCtrlBase::GetDocumentHTML](../Topic/CHtmlEditCtrlBase::GetDocumentHTML.md)|會擷取目前文件的 HTML。|  
|[CHtmlEditCtrlBase::GetDocumentTitle](../Topic/CHtmlEditCtrlBase::GetDocumentTitle.md)|擷取文件的標題。|  
|[CHtmlEditCtrlBase::GetEvent](../Topic/CHtmlEditCtrlBase::GetEvent.md)|擷取介面指標包含資訊與最近一次事件相關的事件物件。|  
|[CHtmlEditCtrlBase::GetEventSrcElement](../Topic/CHtmlEditCtrlBase::GetEventSrcElement.md)|擷取引發事件的物件。|  
|[CHtmlEditCtrlBase::GetFontFace](../Topic/CHtmlEditCtrlBase::GetFontFace.md)|擷取字型名稱對於目前的選取範圍。|  
|[CHtmlEditCtrlBase::GetFontSize](../Topic/CHtmlEditCtrlBase::GetFontSize.md)|擷取目前選取範圍的字型大小。|  
|[CHtmlEditCtrlBase::GetForeColor](../Topic/CHtmlEditCtrlBase::GetForeColor.md)|擷取目前選取範圍的前景色彩 \(文字\)。|  
|[CHtmlEditCtrlBase::GetFrameZone](../Topic/CHtmlEditCtrlBase::GetFrameZone.md)|傳回目前頁面的安全性區域 web 瀏覽器的。|  
|[CHtmlEditCtrlBase::GetIsDirty](../Topic/CHtmlEditCtrlBase::GetIsDirty.md)|表示 HTML 文件是否已變更。|  
|[CHtmlEditCtrlBase::GetShowAlignedSiteTags](../Topic/CHtmlEditCtrlBase::GetShowAlignedSiteTags.md)|傳回影像是否是針對具有 **styleFloat** 屬性的所有項目都會顯示。|  
|[CHtmlEditCtrlBase::GetShowAllTags](../Topic/CHtmlEditCtrlBase::GetShowAllTags.md)|傳回瀏覽器是否會在文件中顯示影像顯示所有標記的位置。|  
|[CHtmlEditCtrlBase::GetShowAreaTags](../Topic/CHtmlEditCtrlBase::GetShowAreaTags.md)|擷取瀏覽器是否顯示區域標記的影像。|  
|[CHtmlEditCtrlBase::GetShowBRTags](../Topic/CHtmlEditCtrlBase::GetShowBRTags.md)|擷取瀏覽器是否顯示 BR\/標記的影像。|  
|[CHtmlEditCtrlBase::GetShowCommentTags](../Topic/CHtmlEditCtrlBase::GetShowCommentTags.md)|擷取瀏覽器是否顯示註解標記的影像。|  
|[CHtmlEditCtrlBase::GetShowMiscTags](../Topic/CHtmlEditCtrlBase::GetShowMiscTags.md)|擷取瀏覽器是否會顯示在 Microsoft Internet Explorer 管理員所顯示的所有標記為 4.0。|  
|[CHtmlEditCtrlBase::GetShowScriptTags](../Topic/CHtmlEditCtrlBase::GetShowScriptTags.md)|擷取瀏覽器是否顯示所有指令碼標記的影像。|  
|[CHtmlEditCtrlBase::GetShowStyleTags](../Topic/CHtmlEditCtrlBase::GetShowStyleTags.md)|擷取瀏覽器是否顯示任何樣式標記的影像。|  
|[CHtmlEditCtrlBase::GetShowUnknownTags](../Topic/CHtmlEditCtrlBase::GetShowUnknownTags.md)|擷取瀏覽器是否顯示所有未知之標籤的圖像。|  
|[CHtmlEditCtrlBase::HorizontalLine](../Topic/CHtmlEditCtrlBase::HorizontalLine.md)|覆寫目前選取範圍的水平線。|  
|[CHtmlEditCtrlBase::HyperLink](../Topic/CHtmlEditCtrlBase::HyperLink.md)|插入目前選取範圍中的超連結。|  
|[CHtmlEditCtrlBase::IE50Paste](../Topic/CHtmlEditCtrlBase::IE50Paste.md)|執行適合貼上作業與 Microsoft Internet Explorer 5. 管理員。|  
|[CHtmlEditCtrlBase::Iframe](../Topic/CHtmlEditCtrlBase::Iframe.md)|覆寫目前選取範圍的內嵌框架。|  
|[CHtmlEditCtrlBase::Image](../Topic/CHtmlEditCtrlBase::Image.md)|覆寫目前選取範圍中的影像。|  
|[CHtmlEditCtrlBase::Indent](../Topic/CHtmlEditCtrlBase::Indent.md)|會將縮排加入選取文字的縮排。|  
|[CHtmlEditCtrlBase::InsFieldSet](../Topic/CHtmlEditCtrlBase::InsFieldSet.md)|覆寫目前選取範圍中的  方塊。|  
|[CHtmlEditCtrlBase::InsInputButton](../Topic/CHtmlEditCtrlBase::InsInputButton.md)|覆寫目前選取範圍上建立按鈕控制項。|  
|[CHtmlEditCtrlBase::InsInputHidden](../Topic/CHtmlEditCtrlBase::InsInputHidden.md)|插入目前選取範圍中的隱藏控制項。|  
|[CHtmlEditCtrlBase::InsInputImage](../Topic/CHtmlEditCtrlBase::InsInputImage.md)|覆寫目前選取範圍的影像控制項。|  
|[CHtmlEditCtrlBase::InsInputPassword](../Topic/CHtmlEditCtrlBase::InsInputPassword.md)|覆寫目前的密碼編譯控制項。|  
|[CHtmlEditCtrlBase::InsInputReset](../Topic/CHtmlEditCtrlBase::InsInputReset.md)|覆寫目前選取範圍的重設控制項。|  
|[CHtmlEditCtrlBase::InsInputSubmit](../Topic/CHtmlEditCtrlBase::InsInputSubmit.md)|覆寫目前選取範圍上建立送出控制項。|  
|[CHtmlEditCtrlBase::InsInputUpload](../Topic/CHtmlEditCtrlBase::InsInputUpload.md)|覆寫目前選取範圍的檔案上載控制項。|  
|[CHtmlEditCtrlBase::Is1DElement](../Topic/CHtmlEditCtrlBase::Is1DElement.md)|判斷元素是否為靜態位置。|  
|[CHtmlEditCtrlBase::Is2DElement](../Topic/CHtmlEditCtrlBase::Is2DElement.md)|判斷元素是否絕對位置。|  
|[CHtmlEditCtrlBase::Italic](../Topic/CHtmlEditCtrlBase::Italic.md)|切換於斜體和 nonitalic 之間切換目前選取範圍。|  
|[CHtmlEditCtrlBase::JustifyCenter](../Topic/CHtmlEditCtrlBase::JustifyCenter.md)|將目前選取範圍的格式區塊。|  
|[CHtmlEditCtrlBase::JustifyLeft](../Topic/CHtmlEditCtrlBase::JustifyLeft.md)|靠左對齊目前選取範圍的格式區塊。|  
|[CHtmlEditCtrlBase::JustifyRight](../Topic/CHtmlEditCtrlBase::JustifyRight.md)|靠右目前選取範圍的格式區塊。|  
|[CHtmlEditCtrlBase::ListBox](../Topic/CHtmlEditCtrlBase::ListBox.md)|覆寫目前選取範圍中的清單方塊中選取控制項。|  
|[CHtmlEditCtrlBase::Marquee](../Topic/CHtmlEditCtrlBase::Marquee.md)|覆寫目前選取範圍上空白跑馬燈。|  
|[CHtmlEditCtrlBase::NewDocument](../Topic/CHtmlEditCtrlBase::NewDocument.md)|建立新的文件。|  
|[CHtmlEditCtrlBase::OrderList](../Topic/CHtmlEditCtrlBase::OrderList.md)|切換的排序清單與一般格式之間的區塊中目前的選取位置。|  
|[CHtmlEditCtrlBase::Outdent](../Topic/CHtmlEditCtrlBase::Outdent.md)|所加入的取消目前的選取範圍格式區塊的縮排。|  
|[CHtmlEditCtrlBase::Paragraph](../Topic/CHtmlEditCtrlBase::Paragraph.md)|覆寫目前選取範圍的分行符號。|  
|[CHtmlEditCtrlBase::Paste](../Topic/CHtmlEditCtrlBase::Paste.md)|覆寫剪貼簿的內容會在目前選取範圍的。|  
|[CHtmlEditCtrlBase::PrintDocument](../Topic/CHtmlEditCtrlBase::PrintDocument.md)|列印目前的文件。|  
|[CHtmlEditCtrlBase::PrintPreview](../Topic/CHtmlEditCtrlBase::PrintPreview.md)|使用預設的預覽列印範本或自訂範本，開啟目前文件的 \[預覽列印\] 視窗。|  
|[CHtmlEditCtrlBase::QueryStatus](../Topic/CHtmlEditCtrlBase::QueryStatus.md)|呼叫這個方法會查詢命令的狀態。|  
|[CHtmlEditCtrlBase::RadioButton](../Topic/CHtmlEditCtrlBase::RadioButton.md)|覆寫目前選取範圍的一個無線控制項。|  
|[CHtmlEditCtrlBase::RefreshDocument](../Topic/CHtmlEditCtrlBase::RefreshDocument.md)|重新整理目前的文件。|  
|[CHtmlEditCtrlBase::RemoveFormat](../Topic/CHtmlEditCtrlBase::RemoveFormat.md)|從目前的選取範圍中移除格式化標記。|  
|[CHtmlEditCtrlBase::SaveAs](../Topic/CHtmlEditCtrlBase::SaveAs.md)|儲存目前 Web 網頁加入至檔案。|  
|[CHtmlEditCtrlBase::SelectAll](../Topic/CHtmlEditCtrlBase::SelectAll.md)|選取整個文件。|  
|[CHtmlEditCtrlBase::Set2DPosition](../Topic/CHtmlEditCtrlBase::Set2DPosition.md)|允許絕對定位項目透過拖曳移動。|  
|[CHtmlEditCtrlBase::SetAbsolutePosition](../Topic/CHtmlEditCtrlBase::SetAbsolutePosition.md)|設定項目的位置屬性「Absolute」或「靜態」。|  
|[CHtmlEditCtrlBase::SetAtomicSelection](../Topic/CHtmlEditCtrlBase::SetAtomicSelection.md)|集合不可部分完成的選取模式。|  
|[CHtmlEditCtrlBase::SetAutoURLDetectMode](../Topic/CHtmlEditCtrlBase::SetAutoURLDetectMode.md)|開啟或關閉自動偵測 URL。|  
|[CHtmlEditCtrlBase::SetBackColor](../Topic/CHtmlEditCtrlBase::SetBackColor.md)|設定目前選取項目的背景色彩。|  
|[CHtmlEditCtrlBase::SetBlockFormat](../Topic/CHtmlEditCtrlBase::SetBlockFormat.md)|設定目前的格式標記。|  
|[CHtmlEditCtrlBase::SetBookMark](../Topic/CHtmlEditCtrlBase::SetBookMark.md)|建立目前選取範圍或插入點的書籤錨定。|  
|[CHtmlEditCtrlBase::SetCSSEditingLevel](../Topic/CHtmlEditCtrlBase::SetCSSEditingLevel.md)|選取  \(層級的 CSS CSS1 或 CSS2\) 編輯器，會支援，如果有的話。|  
|[CHtmlEditCtrlBase::SetDefaultComposeSettings](../Topic/CHtmlEditCtrlBase::SetDefaultComposeSettings.md)|呼叫這個方法會設定為預設的設定。|  
|[CHtmlEditCtrlBase::SetDesignMode](../Topic/CHtmlEditCtrlBase::SetDesignMode.md)|佈景主題模式。|  
|[CHtmlEditCtrlBase::SetDisableEditFocusUI](../Topic/CHtmlEditCtrlBase::SetDisableEditFocusUI.md)|在編輯具有焦點的項目周圍停用已規劃的框線和控制代碼。|  
|[CHtmlEditCtrlBase::SetDocumentHTML](../Topic/CHtmlEditCtrlBase::SetDocumentHTML.md)|設定目前文件的 HTML。|  
|[CHtmlEditCtrlBase::SetFontFace](../Topic/CHtmlEditCtrlBase::SetFontFace.md)|設定目前選取的字型。|  
|[CHtmlEditCtrlBase::SetFontSize](../Topic/CHtmlEditCtrlBase::SetFontSize.md)|設定目前選取範圍的字型大小。|  
|[CHtmlEditCtrlBase::SetForeColor](../Topic/CHtmlEditCtrlBase::SetForeColor.md)|設定目前選取範圍的前景色彩 \(文字\)。|  
|[CHtmlEditCtrlBase::SetIE5PasteMode](../Topic/CHtmlEditCtrlBase::SetIE5PasteMode.md)|設定貼上作業與 Microsoft Internet Explorer Microsoft Internet Explorer 5 相容。.|  
|[CHtmlEditCtrlBase::SetLiveResize](../Topic/CHtmlEditCtrlBase::SetLiveResize.md)|讓瀏覽器在重新調整大小或移動作業期間持續更新項目的外觀。|  
|[CHtmlEditCtrlBase::SetMultiSelect](../Topic/CHtmlEditCtrlBase::SetMultiSelect.md)|啟用多重選取。|  
|[CHtmlEditCtrlBase::SetOverrideCursor](../Topic/CHtmlEditCtrlBase::SetOverrideCursor.md)|絕不命令瀏覽器變更滑鼠指標。|  
|[CHtmlEditCtrlBase::SetOverwriteMode](../Topic/CHtmlEditCtrlBase::SetOverwriteMode.md)|切換外掛程式之間的文字輸入模式和覆寫。|  
|[CHtmlEditCtrlBase::SetRespectVisInDesign](../Topic/CHtmlEditCtrlBase::SetRespectVisInDesign.md)|在設計模式中隱藏不可見的項目。|  
|[CHtmlEditCtrlBase::SetShowAlignedSiteTags](../Topic/CHtmlEditCtrlBase::SetShowAlignedSiteTags.md)|顯示具有 **styleFloat** 屬性之所有項目的影像。|  
|[CHtmlEditCtrlBase::SetShowAllTags](../Topic/CHtmlEditCtrlBase::SetShowAllTags.md)|在文件中顯示影像顯示所有標記的位置。|  
|[CHtmlEditCtrlBase::SetShowAreaTags](../Topic/CHtmlEditCtrlBase::SetShowAreaTags.md)|顯示所有區域標記的影像。|  
|[CHtmlEditCtrlBase::SetShowBRTags](../Topic/CHtmlEditCtrlBase::SetShowBRTags.md)|顯示所有 BR\/標記的影像。|  
|[CHtmlEditCtrlBase::SetShowCommentTags](../Topic/CHtmlEditCtrlBase::SetShowCommentTags.md)|顯示所有註解標記的影像。|  
|[CHtmlEditCtrlBase::SetShowMiscTags](../Topic/CHtmlEditCtrlBase::SetShowMiscTags.md)|顯示在 Microsoft Internet Explorer 管理員所顯示的所有標記為 4.0。|  
|[CHtmlEditCtrlBase::SetShowScriptTags](../Topic/CHtmlEditCtrlBase::SetShowScriptTags.md)|顯示所有指令碼標記的影像。|  
|[CHtmlEditCtrlBase::SetShowStyleTags](../Topic/CHtmlEditCtrlBase::SetShowStyleTags.md)|顯示所有樣式標記的影像。|  
|[CHtmlEditCtrlBase::SetShowUnknownTags](../Topic/CHtmlEditCtrlBase::SetShowUnknownTags.md)|顯示所有未知之標籤的圖像。|  
|[CHtmlEditCtrlBase::TextArea](../Topic/CHtmlEditCtrlBase::TextArea.md)|覆寫目前選取範圍的多行文字輸入控制項。|  
|[CHtmlEditCtrlBase::TextBox](../Topic/CHtmlEditCtrlBase::TextBox.md)|覆寫目前選取範圍上建立文字控制項。|  
|[CHtmlEditCtrlBase::UnBookmark](../Topic/CHtmlEditCtrlBase::UnBookmark.md)|從目前的選取範圍中的所有書籤。|  
|[CHtmlEditCtrlBase::Underline](../Topic/CHtmlEditCtrlBase::Underline.md)|切換加上底線和不加底線之間切換目前選取範圍。|  
|[CHtmlEditCtrlBase::Unlink](../Topic/CHtmlEditCtrlBase::Unlink.md)|從目前的選取範圍中移除所有超連結。|  
|[CHtmlEditCtrlBase::UnorderList](../Topic/CHtmlEditCtrlBase::UnorderList.md)|切換的排序清單與一般格式之間的區塊中目前的選取位置。|  
  
#### 參數  
 `T`  
 衍生類別的名稱。  
  
## 備註  
 **CHtmlEditCtrlBase** 提供編輯命令，例如 [粗體](../Topic/CHtmlEditCtrlBase::Bold.md)瀏覽器的 HTML 提供成員函式。  \(交替，您可以呼叫 [ExecCommand](../Topic/CHtmlEditCtrlBase::ExecCommand.md) 執行 **IDM\_BOLD** 命令\)。  
  
 **CHtmlEditCtrlBase** 不適合單獨站立。  它的設計是公開編輯瀏覽器功能的 HTML 之衍生類別的基底類別 \(請參閱 [CHtmlEditCtrl](../../mfc/reference/chtmleditctrl-class.md) 和 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)\)。  
  
## 繼承階層架構  
 `CHtmlEditCtrlBase`  
  
## 需求  
 **Header:** afxhtml.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [HTMLEdit 範例](../../top/visual-cpp-samples.md)