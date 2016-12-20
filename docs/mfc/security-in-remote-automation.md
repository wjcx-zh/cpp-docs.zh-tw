---
title: "Remote Automation 中的安全性 | Microsoft Docs"
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
  - "啟動物件"
  - "AllowRemoteActivation"
  - "Automation 物件, 安全性選項"
  - "物件啟動"
  - "Remote Automation, 安全性"
  - "安全性 [MFC]"
  - "安全性 [MFC], Remote Automation"
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Remote Automation 中的安全性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遠端 Automation 支援基本安全性層級允許伺服器應用程式撰寫者 \(或是它的系統管理員\) 的特定物件可能如何遠端啟動。  在特定系統的所有 Automation 物件可能將「禁止遠端啟動」或「允許遠端啟動」。  此外，通常會提供個別物件這類功能。  遠端 Automation 使用輸入每個物件的登錄設定， **AllowRemoteActivation**，判斷特定伺服器是否可以遠端啟動。  如果系統範圍設定為使用模式，則在登錄中的每個物件可能會指派這個機碼，因此每一個的個別狀態可能設定是或否適合。  
  
 如果伺服器系統執行 Windows NT 或 Windows 2000，則安全性替代的表單允許。  在這個案例中， Remote Automation 使用 NT 存取控制清單 \(ACL\) \(ACL\) 指定使用者的哪些使用者或群組或群組可能遠端啟動給定的伺服器。  
  
 請注意安全性選項會套用至整個物件;設定特定介面的屬性，或個別的屬性或方法在該物件是不可能的。  
  
 所有安全性選項可能會透過遠端連接 Automation \(RAC\) 管理員設定。  
  
## 請參閱  
 [Remote Automation](../mfc/remote-automation.md)