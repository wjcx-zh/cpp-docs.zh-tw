---
title: "CDocument Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDocument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocument class"
  - "命令處理, documents and"
  - "命令傳送, documents and"
  - "文件 [C++], 命令傳送"
  - "文件 [C++], document classes"
  - "文件 [C++], 多重檢視"
  - "文件 [C++], 序列化"
  - "檔案 [C++], 文件"
  - "序列化 [C++], documents and"
  - "檢視 [C++], 文件"
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CDocument Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

對於使用者定義資料類別的基本功能。  
  
## 語法  
  
```  
class CDocument : public CCmdTarget  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDocument::CDocument](../Topic/CDocument::CDocument.md)|建構 `CDocument` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocument::AddView](../Topic/CDocument::AddView.md)|檢視附加至文件。|  
|[CDocument::BeginReadChunks](../Topic/CDocument::BeginReadChunks.md)|初始化大量讀取。|  
|[CDocument::CanCloseFrame](../Topic/CDocument::CanCloseFrame.md)|進階可覆寫;呼叫會在關閉檢視文件的框架視窗之前。|  
|[CDocument::ClearChunkList](../Topic/CDocument::ClearChunkList.md)|清除大量清單。|  
|[CDocument::ClearPathName](../Topic/CDocument::ClearPathName.md)|清除清單巡覽文件物件。|  
|[CDocument::DeleteContents](../Topic/CDocument::DeleteContents.md)|呼叫執行文件的清除。|  
|[CDocument::FindChunk](../Topic/CDocument::FindChunk.md)|搜尋具有指定之 GUID 的區塊。|  
|[CDocument::GetAdapter](../Topic/CDocument::GetAdapter.md)|會將指標 `IDocument` 物件實作介面。|  
|[CDocument::GetDocTemplate](../Topic/CDocument::GetDocTemplate.md)|會將指標傳至描述文件類型的文件樣板。|  
|[CDocument::GetFile](../Topic/CDocument::GetFile.md)|傳回指向 `CFile` 預期物件。|  
|[CDocument::GetFirstViewPosition](../Topic/CDocument::GetFirstViewPosition.md)|傳回第一個位置在檢視清單;用來開始反覆項目。|  
|[CDocument::GetNextView](../Topic/CDocument::GetNextView.md)|藉由檢視逐一查看清單與文件相關聯的。|  
|[CDocument::GetPathName](../Topic/CDocument::GetPathName.md)|傳回文件的資料檔案的路徑。|  
|[CDocument::GetThumbnail](../Topic/CDocument::GetThumbnail.md)|呼叫以建立縮圖提供者所使用的點陣圖顯示縮圖。|  
|[CDocument::GetTitle](../Topic/CDocument::GetTitle.md)|傳回文件的標題。|  
|[CDocument::InitializeSearchContent](../Topic/CDocument::InitializeSearchContent.md)|呼叫以初始化搜尋處理常式的搜尋內容。|  
|[CDocument::IsModified](../Topic/CDocument::IsModified.md)|指示是否已修改文件，自上次儲存。|  
|[CDocument::IsSearchAndOrganizeHandler](../Topic/CDocument::IsSearchAndOrganizeHandler.md)|告知 `CDocument` 物件執行個體是否為搜尋 \_& 組織建立處理常式。|  
|[CDocument::LoadDocumentFromStream](../Topic/CDocument::LoadDocumentFromStream.md)|呼叫方法來載入資料流的檔案資料。|  
|[CDocument::OnBeforeRichPreviewFontChanged](../Topic/CDocument::OnBeforeRichPreviewFontChanged.md)|呼叫在豐富預覽字型之前變更。|  
|[CDocument::OnChangedViewList](../Topic/CDocument::OnChangedViewList.md)|呼叫，以檢視會從文件中移除。|  
|[CDocument::OnCloseDocument](../Topic/CDocument::OnCloseDocument.md)|呼叫關閉文件。|  
|[CDocument::OnCreatePreviewFrame](../Topic/CDocument::OnCreatePreviewFrame.md)|呼叫框架，當需要建立豐富預覽的預覽畫面。|  
|[CDocument::OnDocumentEvent](../Topic/CDocument::OnDocumentEvent.md)|呼叫框架回應文件事件。|  
|[CDocument::OnDrawThumbnail](../Topic/CDocument::OnDrawThumbnail.md)|在衍生類別中覆寫這個方法會繪製縮圖內容。|  
|[CDocument::OnLoadDocumentFromStream](../Topic/CDocument::OnLoadDocumentFromStream.md)|呼叫由架構，在需要從資料流載入文件資料。|  
|[CDocument::OnNewDocument](../Topic/CDocument::OnNewDocument.md)|呼叫建立新文件。|  
|[CDocument::OnOpenDocument](../Topic/CDocument::OnOpenDocument.md)|透過呼叫來開啟現有的文件。|  
|[CDocument::OnPreviewHandlerQueryFocus](../Topic/CDocument::OnPreviewHandlerQueryFocus.md)|指示預覽處理常式會從呼叫 GetFocus 函式的 HWND。|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](../Topic/CDocument::OnPreviewHandlerTranslateAccelerator.md)|指示預覽處理常式會處理預覽處理常式執行中處理序的訊息幫浦 \(Message Pump\) 傳遞的按鍵。|  
|[CDocument::OnRichPreviewBackColorChanged](../Topic/CDocument::OnRichPreviewBackColorChanged.md)|呼叫，以豐富預覽背景色彩就會變更。|  
|[CDocument::OnRichPreviewFontChanged](../Topic/CDocument::OnRichPreviewFontChanged.md)|呼叫，以豐富預覽已經變更。|  
|[CDocument::OnRichPreviewSiteChanged](../Topic/CDocument::OnRichPreviewSiteChanged.md)|呼叫，以豐富預覽網站已變更。|  
|[CDocument::OnRichPreviewTextColorChanged](../Topic/CDocument::OnRichPreviewTextColorChanged.md)|呼叫，以豐富預覽文字色彩變更。|  
|[CDocument::OnSaveDocument](../Topic/CDocument::OnSaveDocument.md)|呼叫將文件儲存至磁碟。|  
|[CDocument::OnUnloadHandler](../Topic/CDocument::OnUnloadHandler.md)|呼叫框架，其在預覽處理常式卸載。|  
|[CDocument::PreCloseFrame](../Topic/CDocument::PreCloseFrame.md)|呼叫在框架視窗之前關閉。|  
|[CDocument::ReadNextChunkValue](../Topic/CDocument::ReadNextChunkValue.md)|讀取下一個區塊中的值。|  
|[CDocument::ReleaseFile](../Topic/CDocument::ReleaseFile.md)|出現檔案以便讓其他應用程式使用。|  
|[CDocument::RemoveChunk](../Topic/CDocument::RemoveChunk.md)|移除大量使用指定的 GUID。|  
|[CDocument::RemoveView](../Topic/CDocument::RemoveView.md)|中斷連結文件的檢視。|  
|[CDocument::ReportSaveLoadException](../Topic/CDocument::ReportSaveLoadException.md)|進階可覆寫;呼叫，因為例外狀況，在開啟或儲存作業無法完成。|  
|[CDocument::SaveModified](../Topic/CDocument::SaveModified.md)|進階可覆寫;呼叫詢問使用者是否要儲存文件。|  
|[CDocument::SetChunkValue](../Topic/CDocument::SetChunkValue.md)|設定大量值。|  
|[CDocument::SetModifiedFlag](../Topic/CDocument::SetModifiedFlag.md)|設定指定的旗標已修改文件，自上次儲存。|  
|[CDocument::SetPathName](../Topic/CDocument::SetPathName.md)|設定文件所使用的資料檔案的路徑。|  
|[CDocument::SetTitle](../Topic/CDocument::SetTitle.md)|設定這個文件的標題。|  
|[CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md)|告知修改文件中的所有檢視。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)|傳送附加了文件的郵件訊息。|  
|[CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)|如果郵件支援存在，啟用傳送郵件命令。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDocument::m\_bGetThumbnailMode](../Topic/CDocument::m_bGetThumbnailMode.md)|指定 `CDocument` 物件由縮圖 dllhost 的建立。  應該由簽入 `CView::OnDraw`。|  
|[CDocument::m\_bPreviewHandlerMode](../Topic/CDocument::m_bPreviewHandlerMode.md)|指定 `CDocument` 物件由 `Rich Preview`的 prevhost 建立。  應該由簽入 `CView::OnDraw`。|  
|[CDocument::m\_bSearchMode](../Topic/CDocument::m_bSearchMode.md)|指定 `CDocument` 物件由索引子或其他建立搜尋應用程式。|  
|[CDocument::m\_clrRichPreviewBackColor](../Topic/CDocument::m_clrRichPreviewBackColor.md)|指定豐富預覽視窗的背景色彩。  這個色彩會由主應用程式設定。|  
|[CDocument::m\_clrRichPreviewTextColor](../Topic/CDocument::m_clrRichPreviewTextColor.md)|指定豐富預覽視窗的前景色彩。  這個色彩會由主應用程式設定。|  
|[CDocument::m\_lfRichPreviewFont](../Topic/CDocument::m_lfRichPreviewFont.md)|提供豐富預覽視窗指定文字的字型。  這個字型資訊由主應用程式設定。|  
  
## 備註  
 資料表示使用者通常會開啟 \[開啟舊檔\] 命令並儲存檔案儲存訂單資料的單位。  
  
 **CDocument** 支援標準作業，例如建立文件載入和儲存。  這個架構資料作業使用 **CDocument**定義的介面。  
  
 應用程式可以支援一種以上的一種類型的文件，例如，應用程式可能會支援報表和 Word 文件。  文件的每個型別都有相關聯的文件樣板;文件樣板指定哪些資源 \(例如，功能表、圖示或快速鍵 \(Accelerator\) 對應表\) 針對該資料型別使用。  每個文件含有指向其關聯的 `CDocTemplate` 物件。  
  
 使用者與資料互動是透過 [CView](../../mfc/reference/cview-class.md) 與其相關聯的物件。  檢視呈現文件的影像在框架視窗中並解譯為文件中的作業中的使用者輸入。  文件可以具有多個檢視相關聯的。  當使用者開啟文件的視窗時，架構會建立檢視並將其附加至文件。  文件樣板指定哪些檢視和框架視窗是用來顯示文件類型。  
  
 文件是架構的標準命令傳送的一部分而接收來自標準使用者介面元件的命令 \(例如檔案儲存功能表項目\)。  文件現用檢視表轉送的命令。  如果文件不處理該命令，則傳送命令給處理它的文件樣板。  
  
 在修改文件中的資料，其檢視中的每一個都必須以反映這些變更。  **CDocument** 提供 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 成員函式通知檢視的這類變更，因此，檢視可以視需要重新自我繪製。  此架構也會提示使用者在關閉之前儲存已修改的檔案。  
  
 若要實作在典型的應用程式中的資料，您必須執行下列動作:  
  
-   從文件中的每個型別的 **CDocument** 衍生類別。  
  
-   加入成員變數以儲存每個文件的資料。  
  
-   實作讀取和修改文件的資料成員函式。  文件的檢視是這些成員函式的最重要的使用者。  
  
-   覆寫您的文件中類別的 [CObject::Serialize](../Topic/CObject::Serialize.md) 成員函式從磁碟讀取和寫入文件中的資料。  
  
 **CDocument** 透過電子郵件傳送支援您的文件中，如果郵件支援 \(MAPI 存在\)。  請參閱文章 [MAPI](../../mfc/mapi.md) 和 [在 MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
 如需 **CDocument**的資訊，請參閱 [序列化](../../mfc/serialization-in-mfc.md)、 [文件\/檢視架構主題](../../mfc/document-view-architecture.md)和 [文件\/檢視建立](../../mfc/document-view-creation.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDIDOCVW 範例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW 範例](../../top/visual-cpp-samples.md)   
 [MFC NPP 範例](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)