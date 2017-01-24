---
title: "使用類別來編寫 Windows 應用程式 | Microsoft Docs"
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
  - "應用程式 [OLE], MFC 應用程式架構"
  - "資料庫應用程式 [C++], 建立"
  - "MFC [C++], 應用程式開發"
  - "MFC ActiveX 控制項, 建立"
  - "OLE 應用程式 [C++], MFC 應用程式架構"
  - "Windows 應用程式 [C++], MFC 應用程式架構"
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用類別來編寫 Windows 應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Microsoft Foundation 的類別將 \(MFC\) 程式庫組成分類的「應用程式架構」在建立對 Windows 作業系統的應用程式。  在一般層級，架構會定義應用程式的基本架構並提供可以放置在基本架構上的標準使用者介面實作。  您為程式設計人員的工作是填入基本架構的其餘部分，是這些項目是指您的應用程式。  您可以先佔使用 MFC 應用程式精靈建立非常詳盡的起始應用程式的檔案。  您可以使用 Microsoft Visual C\+\+ 資源編輯器設計您的使用者介面項目視覺上，類別檢視命令連接那些項目程式碼和實作應用程式專屬邏輯的類別庫。  
  
 3.0 版和以後 MFC 架構支援 Win32 平台，包括 Microsoft Windows 95 \(含\) 以後版本及 Windows NT 3.51 \(含\) 以後版本。  MFC Win32 支援包含多個執行緒。  如果您需要進行 16 位元程式設計，使用版本 1.5*x* 。  
  
 本文章系列提供應用程式架構廣泛的概觀。  它也探索組成應用程式的主要物件以及如何建立。  在這些文件中包含的主題是下列:  
  
-   [架構](../mfc/framework-mfc.md)。  
  
-   分工在框架和程式碼之間的，如 [在 Framework 建置](../mfc/building-on-the-framework.md)中所述。  
  
-   [應用程式類別](../mfc/cwinapp-the-application-class.md)，封裝應用程式層級的功能。  
  
-   [文件樣板](../mfc/document-templates-and-the-document-view-creation-process.md) 建立及如何處理文件及其相關聯的檢視和框架視窗。  
  
-   [CWnd](../mfc/window-objects.md)類別是所有視窗基底。  
  
-   [圖形物件](../mfc/graphic-objects.md)，例如畫筆和筆刷。  
  
 框架中的其他部分:  
  
-   [視窗物件:概觀](../mfc/window-objects.md)  
  
-   [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
-   [CObject，在 MFC 的基底類別。](../mfc/using-cobject.md)  
  
-   [文件\/檢視架構](../mfc/document-view-architecture.md)  
  
-   [對話方塊](../mfc/dialog-boxes.md)  
  
-   [控制項](../mfc/controls-mfc.md)  
  
-   [控制列](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [記憶體管理](../mfc/memory-management.md)  
  
     除了讓您在 Word 應用程式的一個好處以外對 Windows 作業系統， MFC 也比較容易撰寫特別使用連結和內嵌技術的 OLE 的應用程式。  您可以讓應用程式 OLE 視覺化編輯容器， OLE 視覺化編輯伺服器或兩者，因此，您可以將自動化，如此其他應用程式可以使用應用程式的物件會從遠端巡覽它。  
  
-   [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)  
  
     OLE automation 控制項 Development Kit \(CDK\) 完全現在已經與架構。  本文章系列把 MFC 提供 ActiveX 控制項開發概觀。ActiveX 控制項 \(先前稱為 OLE automation 控制項\)。  
  
-   [資料庫程式設計](../data/data-access-programming-mfc-atl.md)  
  
     MFC 也提供兩組簡化資料存取應用程式的資料庫類別。  使用 ODBC 資料庫類別，您透過開放式資料庫連接 \(ODBC\) 驅動程式可以連接至資料庫，用來為資料集中的資料表和顯示記錄資訊以螢幕上的形式。  使用資料存取物件 \(DAO\) 類別，您可以使用資料庫透過 Microsoft Jet 資料庫引擎或外部 \(非 Jet\) 資料來源，包括 ODBC 資料來源。  
  
     此外， MFC 會撰寫使用 Unicode 和多位元組字元集的應用程式完全啟用 \(MBCS\)，尤其是雙位元組字元集 \(DBCS\)。  
  
 如需 MFC 文件的一般方針，請參閱 [MFC 概觀主題](../mfc/general-mfc-topics.md)。  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)