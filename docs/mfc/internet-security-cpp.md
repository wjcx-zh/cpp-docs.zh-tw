---
title: "網際網路安全性 (C++) | Microsoft Docs"
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
  - "程式碼存取安全性 [C++], 網際網路安全性考量"
  - "程式碼簽署 [C++]"
  - "程式碼簽署 [C++], 網際網路安全性"
  - "數位簽章, 網際網路安全性"
  - "網際網路應用程式, 安全性"
  - "沙箱作業"
  - "安全性 [MFC]"
  - "安全性 [MFC], 網際網路"
  - "Web 應用程式安全性"
  - "Web 應用程式安全性, 網際網路安全性方法"
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 網際網路安全性 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

程式碼安全性是一個主要問題開發人員的和網際網路應用程式的使用者。  有風險:惡意竄改的程式碼、從未知的網站或作者程式碼和程式碼。  
  
 會為網際網路時，有兩種基本方法對安全性。  第一個稱為沙箱」。在這個方法，應用程式限制為一組特定 API，並從潛在危險那些排除例如程式可能終結在使用者的電腦上建立的檔案 I\/O。  使用數位簽章，第二個實作。  這種方法稱為「為網際網路中的縮塑料包裝」。  使用私密金鑰\/公開金鑰技術，則程式碼會驗證並簽署。  在程式碼執行之前，它的數位簽章驗證確定程式碼是從已知驗證來源，因此，程式碼未被修改，因為它簽署。  
  
 在第一種情況，您認為，應用程式不會做任何損害處理，而且您信任應用程式的原點。  在第二個中，數位簽章是用來驗證真實性。  是業界標準之數位簽署識別並提供程式碼發行者的詳細資料。  它的技術以標準，包括 RSA 和 X.509。  如果想要下載並執行來源不明，程式碼瀏覽器通常允許使用者選取。  
  
 如需程式碼簽署和其他安全性措施的其他資訊已經連上網路並可供使用。  資訊可以透過 MSDN Online 網路 Workshop 網站存取， [http:\/\/msdn.microsoft.com\/](http://msdn.microsoft.com/)或透過全球資訊網協會 \(W3C\) 的 [http:\/\/www.w3.org\/](http://www.w3.org/)。  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)