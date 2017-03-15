---
title: "MFC 應用程式精靈所建立的文件和檢視類別 | Microsoft Docs"
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
  - "應用程式精靈 [C++], 建立的文件/檢視類別"
  - "文件類別"
  - "文件類別, 由應用程式精靈建立的"
  - "檢視類別, 由應用程式精靈建立的"
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 應用程式精靈所建立的文件和檢視類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 應用程式精靈會引導您建立基本架構文件和檢視類別可讓您在程式開發的優先順序。  您可以使用 [對應命令和訊息至這些類別](../mfc/reference/mapping-messages-to-functions.md) 和 Visual C\+\+ 原始程式碼編輯器來撰寫其成員函式。  
  
 MFC 應用程式精靈所建立的文件類別是從類別衍生自 [CDocument](../mfc/reference/cdocument-class.md)。  檢視類別會衍生自 [CView](../mfc/reference/cview-class.md)。  名稱應用程式精靈給包含它們的這些類別和檔案會根據您在應用程式精靈對話方塊提供的專案名稱。  在應用程式精靈，您可以使用產生的類別頁面修改預設名稱。  
  
 某些應用程式可能需要多個文件類別、檢視類別或框架視窗類別。  如需詳細資訊，請參閱 [許多資料型別、檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)