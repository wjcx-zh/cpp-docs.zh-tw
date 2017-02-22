---
title: "使用者定義的處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.handlers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_MESSAGE 巨集"
  - "ON_REGISTERED_MESSAGE 巨集"
  - "使用者定義的處理常式"
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 使用者定義的處理常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列對應項目對應至函式原型。  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_MESSAGE \( \<訊息\>， \<memberFxn\> \)|afx\_msg LRESULT memberFxn \(WPARAM， LPARAM\);|  
|ON\_REGISTERED\_MESSAGE \( \<nMessageVariable\>， \<memberFxn\> \)|afx\_msg LRESULT memberFxn \(WPARAM， LPARAM\);|  
|ON\_THREAD\_MESSAGE \( \<訊息\>， \<memberFxn\> \)|afx\_msg 空 memberFxn \(WPARAM， LPARAM\);|  
|ON\_REGISTERED\_THREAD\_MESSAGE \( \<nMessageVariable\>， \<memberFxn\> \)|afx\_msg 空 memberFxn \(WPARAM， LPARAM\);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)