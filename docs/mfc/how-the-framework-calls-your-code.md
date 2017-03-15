---
title: "架構如何呼叫您的程式碼 | Microsoft Docs"
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
  - "應用程式特定事件 [C++]"
  - "命令處理, 在 MFC 中呼叫處理常式和程式碼"
  - "命令傳送, 架構"
  - "命令傳送, MFC"
  - "控制流程 [C++], MFC 架構和您的程式碼"
  - "事件 [C++], MFC 中的命令路由"
  - "事件 [C++], 事件驅動型程式設計"
  - "MFC [C++], 呼叫程式碼"
  - "MFC [C++], 呼叫程式碼來源"
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 架構如何呼叫您的程式碼
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

了解 MFC 架構中您的原始程式碼和程式碼之間的關聯性很重要。  當應用程式執行時，大部分的控制流程位於框架中的程式碼。  當使用者選取命令並編輯檢視中的資料，架構處理從視窗收到訊息的訊息迴圈。  架構可以自行處理的事件根本不取決於您的程式碼。  例如，架構知道如何回應使用者命令來關閉視窗並結束應用程式。  當它處理這些工作時，架構會使用訊息處理常式和 C\+\+ 虛擬函式讓您有機會回應這些事件。  您的程式碼並不在控制中；然而這個框架是的。  
  
 架構會呼叫您的應用程式特定事件的程式碼。  例如，當使用者選取命令時，架構會沿著 C\+\+ 物件序列的順序：目前檢視和框架視窗、與檢視關聯的文件、文件的文件範本和應用程式物件。  如果其中一個物件可以處理命令，則它會呼叫適當的訊息處理函式。  對於任何指定的命令，呼叫的程式碼可能是您的、也可能是架構的。  
  
 這個安排對於有傳統的視窗或事件驅動的程式設計經驗的人來說，應該是有些熟悉的。  
  
 在相關主題中，您將讀取本框架在初始化和執行應用程式時會做什麼，然後會在應用程式結束時清除。  您也會了解程式碼要在何處寫入調整。  
  
 如需詳細資訊，請參閱 [類別 CWinApp：應用程式類別。](../mfc/cwinapp-the-application-class.md) 和 [資料範本與文件\/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 請參閱  
 [在架構上建置](../mfc/building-on-the-framework.md)