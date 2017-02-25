---
title: "MFC 應用程式架構類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式架構類別"
  - "類別 [C++], MFC"
  - "MFC [C++], 應用程式開發"
  - "MFC [C++], 類別"
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 應用程式架構類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在這個類別會使架構應用程式的結構。  它們提供常用的功能給大部分的應用程式。  您填入架構將應用程式特定的功能。  一般來說，您會藉由衍生新類別從結構描述，然後將新的成員或覆寫現有的成員函式來進行。  
  
 [應用程式精靈](../mfc/reference/mfc-application-wizard.md) 產生應用程式的幾種型別，以不同方式使用應用程式架構。  SDI \(單一文件介面\) 和 MDI \(多重文件介面\) 應用程式充分利用呼叫文件的架構的部分\/檢視架構。  應用程式的其他型別，例如對話方塊架構的應用程式，表單架構應用程式，因此DLL使用少數文件\/檢視架構的功能。  
  
 文件\/檢視應用程式包含一或多組文件、檢視和框架視窗。  文件樣板物件會將每一個文件\/檢視架構\/集合的類別。  
  
 雖然您在 MFC 應用程式不使用文件\/檢視架構，不過還是有一些優點值得如此做。  MFC OLE 容器和伺服器支援根據文件\/檢視架構，例如支援列印和預覽列印。  
  
 所有的 MFC 應用程式中至少有兩個物件:衍生自 [CWinApp](../mfc/reference/cwinapp-class.md)的應用程式物件和某一個主視窗物件，取得 \(通常間接\) 從 [CWnd](../mfc/reference/cwnd-class.md)。\(通常，主視窗從 [CFrameWnd](../mfc/reference/cframewnd-class.md)、 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)或 [CDialog](../mfc/reference/cdialog-class.md)衍生的型別，衍生自 `CWnd`\)。  
  
 使用文件\/檢視架構包含其他物件的應用程式。  主要物件如下:  
  
-   衍生自的應用程式物件 [CWinApp](../mfc/reference/cwinapp-class.md)，如上所述。  
  
-   從類別衍生的一個或多個資料類別 [CDocument](../mfc/reference/cdocument-class.md)物件。  文件類別物件於檢視操作資料的內部表示負責。  它們可能與資料檔案。  
  
-   衍生自類別的一或多個檢視物件 [CView](../mfc/reference/cview-class.md)。  每個檢視是附加到文件並與框架視窗。  檢視顯示和管理文件類別物件的資料。  
  
 文件\/檢視應用程式也包含框架視窗 \(衍生自 [CFrameWnd](../mfc/reference/cframewnd-class.md)\) 和文件範本 \(衍生自 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)\)。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)