---
title: "TN025：文件、檢視和框架建立 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.creation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件, 檢視和框架建立"
  - "TN025"
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN025：文件、檢視和框架建立
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個會描述 WinApps、DocTemplates、文件、架構和檢視的建立和所有權限問題。  
  
## WinApp  
 在系統中有一個 `CWinApp` 物件。  
  
 由 `WinMain`的框架的內部實作靜態建構及初始化。  您必須衍生自 `CWinApp` 做有用的任何例外狀況:擴充 DLL 不應該有 `CWinApp` 執行個體 \(在 `DllMain` 完成\)。  
  
 一個 `CWinApp` 物件擁有文件樣板 \( `CPtrList`\) 清單。  有一或多個文件樣板每個應用程式。  DocTemplates 從資源檔 \(即字串陣列\) 通常在載入至 `CWinApp::InitInstance`。  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);  
AddDocTemplate(pTemplate);  
```  
  
 一個 `CWinApp` 物件擁有在應用程式中的所有框架視窗。  在 **CWinApp::m\_pMainWnd**應該儲存應用程式的主框架視窗;通常您在 `InitInstance` 實作的集合則為 `m_pMainWnd` ，如果尚未讓 AppWizard 執行它。  對於單一文件介面 \(SDI\) 這是做為主要應用程式框架視窗以及唯一的文件框架視窗的 `CFrameWnd` 。  如果是多重文件介面 \(MDI\) \(MDI\) 這是 MDI 框架 \( `CMDIFrameWnd`類別\) 做為包含所有子系 `CFrameWnd`. 的主要應用程式框架視窗。  每個子視窗是 `CMDIChildWnd` 類別 \(衍生自 `CFrameWnd`\) 以及可能太多文件框架視窗之一。  
  
## DocTemplates  
 `CDocTemplate` 是文件的建立者和管理員。  它擁有它所建立的文件。  如果您的應用程式使用以下這種架構資源的方法，它不會需要衍生自 `CDocTemplate`。  
  
 對於 SDI 應用程式，類別 `CSingleDocTemplate` 記錄一個開啟的文件。  對於 MDI 應用程式，類別 `CMultiDocTemplate` 保留一份清單 \( `CPtrList`從該範本建立的\) 所有目前開啟的文件。  `CDocTemplate::AddDocument` 和 `CDocTemplate::RemoveDocument` 為加入或移除文件的虛擬成員函式從範本。  `CDocTemplate` 是 **CDocument** 的 friend，因此我們可以設定保護 **CDocument::m\_pDocTemplate** 返回指標點回到建立文件的文件範本。  
  
 `CWinApp` 處理預設的 `OnFileOpen` 實作，這會查詢所有文件範本。  實作包含尋找已開啟的文件和決定開啟新文件的儲存格式。  
  
 `CDocTemplate` 管理文件和架構 UI 的繫結。  
  
 `CDocTemplate` 保留未命名的文件數目計數。  
  
## CDocument  
 **CDocument** `CDocTemplate`所擁有。  
  
 文件有檢視文件目前開啟之檢視的清單 \(衍生自 `CView`\) \( `CPtrList`\)。  
  
 文件不建立\/終結檢視，不過，它們互相附加，在建立之後。  當文件關閉 \(透過檔案\/關閉\)，所有附加的檢視將會關閉。  當在文件中的最後一個檢視關閉 \(即視窗\/關閉\) 文件即將關閉。  
  
 `CDocument::AddView`， `RemoveView` 介面來維護檢視清單。  **CDocument** 是 `CView` 的 friend，因此我們可以設定 **CView::m\_pDocument** 返回指標。  
  
## CFrameWnd  
 `CFrameWnd` \(也稱為框架\) 播放角色與在 MFC 1.0 中，不過， `CFrameWnd` 類別現在是設計在許多情況下使用，而不需要從衍生新的類別。  衍生類別 \(Derived Class\) `CMDIFrameWnd` 和 `CMDIChildWnd` 也會引發許多標準命令已經實作。  
  
 `CFrameWnd` 物件會在框架工作區的視窗執行。  通常會填入框架工作區的主視窗。  
  
 對於 MDI 框架視窗，工作區填滿又是所有 MDI 子框架視窗的 MDICLIENT 父控制項。  對於 SDI 框架視窗或 MDI 子框架視窗，工作區通常填滿 `CView`衍生的 Window 物件。  在 `CSplitterWnd`的情況下，這個檢視的工作區填滿 `CSplitterWnd` 視窗物件和 `CView`衍生的視窗物件 \(每分割窗格\) 建立為 `CSplitterWnd`的子視窗。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)