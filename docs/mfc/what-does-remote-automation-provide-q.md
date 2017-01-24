---
title: "Remote Automation 提供什麼功能？ | Microsoft Docs"
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
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation 提供什麼功能？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遠端自動化允許程式叫用電腦上 `IDispatch` 實作的類別。  它也支援 Automation 需要的其他介面，尤其是集合支援的 **IEnumVARIANT** 。  當然不提供發出其他 COM 介面，除了 **IUnknown**\)，而且像一般 Automation，它包含封送處理只支援 Automation 支援的資料型別。  
  
 這套工具可以讓程式碼存取的方法和屬性，包括傳回集合或提高自動化物件在可存取的 Web 節點的物件項目。  如果用戶端也執行適當的軟體，用於伺服器可能會對回呼至用戶端，再使用自動化功能 \(此為只有 32 位元和 64 位元用戶端的運作方式，並在概念上類似的對事件，不過它不會使用同一個機制\)。  
  
 對於應用程式能夠為遠端 Automation 伺服程式，必須實作為可執行檔 \(即為「本機伺服器」而不是「inproc 伺服器」\)。  
  
## 請參閱  
 [Remote Automation 適用於什麼情況？](../mfc/where-does-remote-automation-fit-in-q.md)   
 [DCOM 的歷史](../mfc/history-of-dcom.md)