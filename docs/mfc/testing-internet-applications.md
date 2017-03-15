---
title: "測試網際網路應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯 [MFC], Web 應用程式"
  - "偵錯 Web 應用程式, 測試應用程式"
  - "網際網路偵錯和測試"
  - "測試, 網際網路應用程式"
  - "Web 應用程式, 測試"
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 測試網際網路應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在網際網路上有一些獨一無二的測試挑戰，特別是在 Web 伺服器上執行的應用程式。  您初始測試可能會使用單一使用者的用戶端連接到測試伺服器。  這對於偵錯您的程式碼將會非常有用。  
  
 您也會想要在實際的情況下測試:當多個用戶端連接在高速連接以及低速循序的線路，包括數據機連接。  模擬虛擬的情況非常困難，不過，值得花時間設計可能情況並執行它們。  可能的話，您可能會想要使用工具做容量和壓力測試。  某些錯誤類別，例如時間 Bug，很難尋找並重新產生。  
  
 其中一個網際網路程式設計挑戰在於其可視性。  對網站的許多存取可能會減慢伺服器。  您會希望伺服器緩慢地降速。  如果您的應用程式失敗 \(例如，資料損毀，當寫入登錄，或是寫入時 Cookie 在用戶端\)，您要避免可能會對使用者的電腦造成破壞性的任何事情。  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)