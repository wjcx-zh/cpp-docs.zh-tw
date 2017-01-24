---
title: "Displaying Assertions | Microsoft Docs"
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
  - "判斷提示, 偵錯"
  - "判斷提示, 顯示"
  - "偵錯 [ATL], displaying assertions"
  - "偵錯判斷提示"
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Displaying Assertions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果用戶端連接至您的服務會停止回應，服務可能會判斷  和  會顯示訊息方塊則無法檢視。  您可以確認這種使用 Visual C\+\+ 的偵錯工具偵錯程式碼 \(請參閱 [使用工作管理員](../atl/using-task-manager.md) 前一節\)。  
  
 如果您決定您的服務會顯示您看到的訊息方塊，您可能會想要在重複使用服務之前設定 **Allow Service to Interact with Desktop** 選項。  這個選項是允許服務顯示的所有訊息方塊出現在桌面上開始的參數。  若要設定這個選項，請開啟服務控制台應用程式，請選取服務，按一下  **啟動**，然後選取 **Allow Service to Interact with Desktop** 選項。  
  
## 請參閱  
 [Debugging Tips](../atl/debugging-tips.md)