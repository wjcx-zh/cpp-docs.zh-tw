---
title: "CView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "子視窗, 檢視"
  - "CView class"
  - "document/view architecture"
  - "frame windows [C++], 檢視"
  - "輸入, and view class"
  - "MDI [C++], view windows"
  - "多重檢視"
  - "預覽列印, view windows"
  - "user input [C++], interpreting through view class"
  - "檢視 [C++], view classes"
  - "windows [C++], 檢視"
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為使用者定義的檢視類別的基本功能。  
  
## 語法  
  
```  
class AFX_NOVTABLE CView : public CWnd  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CView::CView](../Topic/CView::CView.md)|建構 `CView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CView::DoPreparePrinting](../Topic/CView::DoPreparePrinting.md)|顯示列印對話方塊並建立印表機內容;呼叫時，覆寫 `OnPreparePrinting` 成員函式時。|  
|[CView::GetDocument](../Topic/CView::GetDocument.md)|傳回文件與檢視。|  
|[CView::IsSelected](../Topic/CView::IsSelected.md)|測試文件項目是否已選取。  要求為 OLE 支援。|  
|[CView::OnDragEnter](../Topic/CView::OnDragEnter.md)|呼叫，則項目第一次被拖曳到檢視的拖放區域。|  
|[CView::OnDragLeave](../Topic/CView::OnDragLeave.md)|呼叫，只要拖曳的項目離開檢視的拖放區域。|  
|[CView::OnDragOver](../Topic/CView::OnDragOver.md)|呼叫，以在拖曳項目至檢視的拖放區域。|  
|[CView::OnDragScroll](../Topic/CView::OnDragScroll.md)|呼叫來決定游標是否拖曳至  視窗中捲動區域。|  
|[CView::OnDrop](../Topic/CView::OnDrop.md)|呼叫，當項目丟棄拖放到檢視的區域，預設的處理常式。|  
|[CView::OnDropEx](../Topic/CView::OnDropEx.md)|呼叫，當項目丟棄拖放到檢視的區域，主要的處理常式。|  
|[CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)|呼叫，以檢視先附加至文件之後。|  
|[CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)|呼叫，以 `OnDraw` 成員函式以顯示於螢幕或 `OnPrint` 成員函式之前呼叫或使用來列印預覽列印呼叫。|  
|[CView::OnScroll](../Topic/CView::OnScroll.md)|呼叫時， OLE 項目在檢視中的邊界之外拖曳。|  
|[CView::OnScrollBy](../Topic/CView::OnScrollBy.md)|呼叫，以包含現用就地 OLE 項目的檢視移動。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CView::OnActivateFrame](../Topic/CView::OnActivateFrame.md)|呼叫，以包含這個檢視的框架視窗中啟用或停用。|  
|[CView::OnActivateView](../Topic/CView::OnActivateView.md)|呼叫，以檢視啟動。|  
|[CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)|呼叫時，列印工作開始;覆寫配置圖形裝置介面 \(GDI\) 資源。|  
|[CView::OnDraw](../Topic/CView::OnDraw.md)|呼叫轉譯文件的影像螢幕顯示、印表機、預覽列印的。  需要的實作。|  
|[CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)|呼叫時，列印工作結束;覆寫解除配置 GDI 資源。|  
|[CView::OnEndPrintPreview](../Topic/CView::OnEndPrintPreview.md)|呼叫，以預覽模式結束。|  
|[CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)|呼叫，或在列印文件中預覽之前，初始化列印對話方塊的覆寫。|  
|[CView::OnPrint](../Topic/CView::OnPrint.md)|呼叫或列印預覽文件的頁面。|  
|[CView::OnUpdate](../Topic/CView::OnUpdate.md)|呼叫以告知檢視修改的檔案。|  
  
## 備註  
 檢視附加至文件並做為文件和使用者之間的媒介:這個檢視呈現文件的影像在螢幕或印表機上並解譯為作業中的使用者輸入文件。  
  
 檢視是框架視窗的子系。  在分隔視窗的情況下，多個檢視都可以共用框架視窗 \(Frame Window\)。  檢視類別、框架視窗類別和資料類別之間的關聯性。 `CDocTemplate` 建立物件。  當使用者開啟新視窗或將現有專案時，架構會建構一個新的檢視並將其附加至文件。  
  
 檢視只能附加至文件，例如，但文件中可以有多個檢視同時附加至的話\)，則為，如果文件顯示在分隔視窗或在多重文件介面 \(MDI\) \(MDI\) 應用程式中多子視窗。  您的應用程式可以支援檢視不同類型的特定資料型別的，例如，有文字處理程式可能會提供文件執行全文檢索檢視，而且大綱檢視只會顯示標題區段。  如果使用了分隔視窗，檢視這些不同類型的可放置在個別的框架視窗或在單一框架視窗中分離窗格。  
  
 檢視可能會負責處理輸入多種不同類型，例如型別、滑鼠輸入或從功能表、工具列或捲軸的輸入會透過拖放功能，以及命令。  檢視收到框架視窗轉送的命令。  如果檢視無法處理特定命令，就會傳送這個命令會將其相關聯的文件。  如同所有命令目標，檢視透過訊息對應的處理訊息。  
  
 這個檢視負責顯示和修改文件中的資料，但不儲存它。  文件提供檢視有關其資料的必要詳細資料。  您可以直接讓檢視存取文件中的資料成員，也可以使用做為檢視類別。提供文件類別的成員函式來呼叫。  
  
 當文件中的資料變更時，檢視負責變更通常會呼叫文件中的 [CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 函式，會呼叫每個的 `OnUpdate` 成員函式告知任何其他檢視。  `OnUpdate` 的預設實作會失效檢視的整個工作區 \(Client Area\)。  您可以覆寫它失效對應至文件之修改的部分工作區的那些區域。  
  
 若要使用 `CView`，請從衍生類別並實作 `OnDraw` 成員函式執行螢幕顯示。  您也可以使用 `OnDraw` 執行列印和預覽列印。  這個架構處理列印和預覽列印文件的迴圈。  
  
 檢視處理 [CWnd::OnHScroll](../Topic/CWnd::OnHScroll.md) 和 [CWnd::OnVScroll](../Topic/CWnd::OnVScroll.md) 成員函式的捲軸訊息。  您可以實作捲軸訊息處理這些函式，您也可以使用 `CView` 衍生類別 [CScrollView](../../mfc/reference/cscrollview-class.md) 管理您的捲動。  
  
 除了 `CScrollView`以外， MFC 程式庫提供從 `CView`衍生的其他九個類別:  
  
-   [CCtrlView](../../mfc/reference/cctrlview-class.md)，讓文件可以使用來檢視樹狀目錄、清單和 Rich Edit 控制項檢視結構。  
  
-   [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，顯示  對話方塊中的資料庫資料錄檢視的控制項。  
  
-   [CEditView](../../mfc/reference/ceditview-class.md)，提供簡單的多行文字編輯器中的檢視。  您可以使用 `CEditView` 物件當做控制項在對話方塊中並在文件的檢視。  
  
-   包含[CFormView](../../mfc/reference/cformview-class.md)對話方塊控制項和根據對話方塊樣板資源可捲動的檢視。  
  
-   [CListView](../../mfc/reference/clistview-class.md)，讓文件可以使用來檢視在清單控制項檢視結構。  
  
-   [CRecordView](../../mfc/reference/crecordview-class.md)，顯示  對話方塊中的資料庫資料錄檢視的控制項。  
  
-   [CRichEditView](../../mfc/reference/cricheditview-class.md)，讓文件可以使用來檢視 Rich Edit 控制項檢視結構。  
  
-   [CScrollView](../../mfc/reference/cscrollview-class.md)，會自動提供捲動功能支援的檢視。  
  
-   [CTreeView](../../mfc/reference/ctreeview-class.md)，讓文件可以使用來檢視樹狀目錄控制項檢視結構。  
  
 `CView` 類別也有衍生自的類別實作名為 **CPreviewView**，架構會用來執行預覽列印。  這個類別提供唯一的功能提供支援加入至預覽列印視窗，例如  工具列中，按一下或雙重網頁預覽和縮放，也就是說，擴充預覽的影像。  您不需要呼叫或覆寫任何 CPreviewView 的成員函式，除非您想要實作您自己的預覽列印的介面 \(例如，因此，如果您要支援編輯在預覽列印模式\)。  如需使用 `CView`的資訊，請參閱 [文件\/檢視架構](../../mfc/document-view-architecture.md) 和 [列印](../../mfc/printing.md)。  如需詳細的額外資訊，請參閱 [Technical Note 30](../../mfc/tn030-customizing-printing-and-print-preview.md) 在自訂的預覽列印。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC MDIDOCVW 範例](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)