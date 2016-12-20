---
title: "MFC 物件關聯性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 物件關聯性"
  - "MFC, 索引鍵物件之間的關聯性"
  - "物件 [C++], 關聯性"
  - "關聯性, MFC 物件"
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 物件關聯性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了協助將文件\/檢視建立程序在檢視方塊，請考慮執行程式:文件框架視窗用來包含檢視和檢視關聯的文件。  
  
-   文件保留該資料和指標檢視清單來建立文件的文件範本。  
  
-   檢視保留指標對其資料並為其父框架視窗的子系。  
  
-   文件框架視窗保留指標為其目前現用檢視表。  
  
-   文件樣板保留其開啟的文件清單。  
  
-   應用程式保留它的文件範本清單。  
  
-   視窗記錄所有開啟的視窗，因此可以傳送訊息給它們。  
  
 這些關聯性文件\/檢視建立期間建立。  下表顯示執行中程式的物件如何存取其他物件。  任何物件都可以藉由呼叫全域函式 [AfxGetApp](../Topic/AfxGetApp.md) 取得應用程式物件的指標。  
  
### 存取在應用程式中其他物件  
  
|來自物件|如何存取其他物件|  
|----------|--------------|  
|Document|使用 [GetFirstViewPosition](../Topic/CDocument::GetFirstViewPosition.md) 和 [GetNextView](../Topic/CDocument::GetNextView.md) 存取文件的檢視清單。<br /><br /> 呼叫取得文件範本的 [GetDocTemplate](../Topic/CDocument::GetDocTemplate.md) 。|  
|檢視|呼叫以取得文件中的 [GetDocument](../Topic/CView::GetDocument.md) 。<br /><br /> 呼叫取得框架視窗的 [GetParentFrame](../Topic/CWnd::GetParentFrame.md) 。|  
|文件框架視窗|呼叫 [GetActiveView](../Topic/CFrameWnd::GetActiveView.md) 以取得目前檢視。<br /><br /> 呼叫 [GetActiveDocument](../Topic/CFrameWnd::GetActiveDocument.md) 以取得文件附加至目前的檢視。|  
|MDI 框架視窗|呼叫 [MDIGetActive](../Topic/CMDIFrameWnd::MDIGetActive.md) 以取得目前啟動中的 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。|  
  
 通常，框架視窗有一個檢視，不過有時候，在分隔視窗中同一個框架視窗包含多個檢視。  框架視窗保留目前啟用檢視的指標；指標會在檢視啟動時的任何時候進行更新。  
  
> [!NOTE]
>  儲存在 [m\_pMainWnd](../Topic/CWinThread::m_pMainWnd.md) 應用程式物件的成員變數中的主框架視窗的指標。  在`InitInstance` 的複寫中呼叫`OnFileNew` 會讓`CWinApp` 的成員函式幫你設好`m_pMainWnd`。  如果您未呼叫 `OnFileNew`，則必須設定 `InitInstance` 的變數值。如果 \/Embedding 在命令列上，則 \(SDI COM 元件 \(伺服器\) 應用程式可能無法設定變數。請注意 `m_pMainWnd` 現在是 `CWinThread` 類別的成員而非 `CWinApp` 類別。  
  
## 請參閱  
 [文件範本和文件\/檢視建立流程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文件樣板建立](../mfc/document-template-creation.md)   
 [文件\/檢視建立](../mfc/document-view-creation.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)