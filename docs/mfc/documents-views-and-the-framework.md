---
title: "文件、檢視和架構 | Microsoft Docs"
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
  - "應用程式物件 [C++], 與其他 MFC 物件的關聯"
  - "應用程式 [MFC]"
  - "文件物件, 與其他 MFC 物件相關的"
  - "文件樣板, 範本物件"
  - "文件/檢視架構, 關於文件/檢視架構"
  - "文件 [C++]"
  - "MFC [C++], 應用程式架構"
  - "MFC [C++], 文件"
  - "MFC [C++], 檢視"
  - "MFC 物件關聯性"
  - "物件 [C++], MFC 應用程式"
  - "執行緒物件"
  - "檢視物件, 與其他 MFC 物件的關聯"
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件、檢視和架構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 架構核心是文件和檢視的概念。  文件是使用者在編輯工作階段互動的資料物件。  它是由 `New` 或 **檔案** 功能表上的 **Open** 命令所建立，通常會被儲存在檔案中。\(衍生自類別 **CDocument** 的標準 MFC 文件與 Active 文件和 OLE 複合文件不同。\)檢視是使用者與文件互動的視窗物件。  
  
 執行中應用程式的主要物件如下：  
  
-   文件或多個文件。  
  
     您的文件類別 \(衍生自 [CDocument](../mfc/reference/cdocument-class.md)\) 指定您的應用程式資料。  
  
     如果您想要在應用程式使用 OLE 功能，從 [COleDocument](../mfc/reference/coledocument-class.md) 或其中一個它的衍生類別衍生您的文件類別，根據您需要的功能類型。  
  
-   檢視或多個檢視。  
  
     檢視類別 \(衍生自 [CView](../mfc/reference/cview-class.md)\) 是使用者的「資料上的視窗」。檢視類別控制使用者如何參閱文件資料並與其互動。  在某些情況下，您可能想要文件有多個資料檢視。  
  
     如果您需要捲動，從 [CScrollView](../mfc/reference/cscrollview-class.md) 衍生。  如果您要在對話方塊樣板資源配置使用者介面，從 [CFormView](../mfc/reference/cformview-class.md) 衍生。  對於簡單的文字資料，請使用 [CEditView](../mfc/reference/ceditview-class.md) 或從其衍生。  如需表單架構的資料存取應用程式，例如資料輸入程式，從 [CRecordView](../mfc/reference/crecordview-class.md) \(ODBC\) 衍生。  類別 [CTreeView](../mfc/reference/ctreeview-class.md)、[CListView](../mfc/reference/clistview-class.md) 和 [CRichEditView](../mfc/reference/cricheditview-class.md) 也可使用。  
  
-   框架視窗  
  
     檢視是顯示在「文件框架視窗」內部。在 SDI 應用程式中，文件框架視窗也是應用程式的「主框架視窗」。  在 MDI 應用程式中，文件視窗是會顯示在主框架視窗內的子視窗。  您的衍生的主框架視窗類別會指定樣式和包含檢視的框架視窗的其他特性。  如果您需要自訂框架視窗，從 [CFrameWnd](../mfc/reference/cframewnd-class.md) 衍生以自訂 SDI 應用程式的文件框架視窗。  從 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 衍生以自訂 MDI 應用程式的主框架視窗。  同時從 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 衍生一個類別以自訂應用程式支援的每一種不同的 MDI 文件框架視窗。  
  
-   文件範本或範本  
  
     資料範本組織在文件、檢視和框架視窗建立的時候。  特定文件樣板類別 \(衍生自 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)類別\) 建立並管理一個型別的所有開啟的文件。  支援多個文件型別的應用程式擁有多個文件範本。  為 SDI 應用程式使用類別 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) 或為 MDI 應用程式使用 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) 類別。  
  
-   應用程式物件  
  
     您的應用程式類別 \(衍生自 [CWinApp](../mfc/reference/cwinapp-class.md)\) 控制所有上述物件並指定應用程式的行為 \(例如初始化和清除\)。  應用程式的唯一應用程式物件建立及管理應用程式支援的任何資料型別的文件範本。  
  
-   執行緒物件  
  
     如果您的應用程式建立個別的執行緒 \(例如，在背景執行計算\) ，您將使用衍生自 [CWinThread](../mfc/reference/cwinthread-class.md) 的類別。  [CWinApp](../mfc/reference/cwinapp-class.md) 衍生自 `CWinThread` 並表示應用程式執行 \(或主要\) 的處理序主執行緒。  您也可以在次要執行緒使用 MFC。  
  
 在執行中的應用程式，這些物件一起合作地回應使用者動作，並透過命令和其他訊息繫結在一起。  單一應用程式物件處理一個或多個資料範本。  每個文件樣板建立和管理一個或多個資料 \(根據應用程式是否是 SDI 或 MDI\)。  使用者透過框架視窗中的檢視來檢視和操作資料。  下圖顯示 SDI 應用程式中這些物件之間的關聯性。  
  
 ![執行中 SDI 應用程式內的物件](../mfc/media/vc386v1.png "vc386V1")  
執行中的 SDI 應用程式內的物件  
  
 這系列的其他文章說明架構工具、MFC 應用程式精靈和資源編輯器，如何建立這些物件、它們如何一起工作，以及如何在您的程式設計中使用它們。  文件、檢視和框架視窗在 [視窗物件](../mfc/window-objects.md) 和 [文件\/檢視架構](../mfc/document-view-architecture.md) 中會進一步討論。  
  
## 請參閱  
 [使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)