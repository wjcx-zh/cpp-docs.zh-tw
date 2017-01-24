---
title: "Remote Automation 適用於什麼情況？ | Microsoft Docs"
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
  - "Remote Automation, DCOM"
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation 適用於什麼情況？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DCOM 在 1996 年放開並只對 32 位元和 64 位元平台上可用。  在 Microsoft Visual Basic 小組一定會看到 Visual Basic 使用允許的自動化其元件進行通訊。  缺少分散式版本嚴格限制了使用在企業環境中的這些功能，因此，開發 Visual Basic 4.0 企業版的小組決定調查它自己的建立 OLE 和 COM 的 Automation 組件的遠端元件。  清楚地，主要目標是確保結果與相容並且可以由 DCOM 取代，可用時。  並繼續實作 16 位元和 32 位元 Windows 平台的遠端 Automation \(RA\)。  
  
 遠端自動化未繫結至任何特定語言，不過，直到 Visual C\+\+ 4.2 企業版，它僅隨附於 Visual Basic 4.0。  請注意遠端 Automation 是 DCOM 整個屬於。  如果您有機會使用 DCOM 而非遠端自動化在應用程式中，您應該這樣做。  然而，有遠端 Automation 是更適當的案例:  
  
-   無論位於何處有 16 位用戶端。  
  
-   如果您的組織不會在 Windows NT 或 Windows 95 DCOM 允許版本。  
  
-   如果您升級使用遠端自動化在一個或多個 Visual Basic 元件位置使用 C\+\+ 元件中的現有應用程式組。  
  
 必須在建立的程式建立使用遠端自動化與之間沒有差異會使用 DCOM 的 Automation，，和設定程序變得非常簡單交換作業在遠端自動化和 DCOM 之間。  因此，，一旦基礎結構之後，從遠端 Automation 應用程式升級至 DCOM 不困難。  
  
## 請參閱  
 [Remote Automation 提供什麼功能？](../mfc/what-does-remote-automation-provide-q.md)   
 [DCOM 的歷史](../mfc/history-of-dcom.md)