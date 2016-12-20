---
title: "SOCKADDR 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SOCKADDR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SOCKADDR 結構"
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SOCKADDR 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`SOCKADDR` 結構是用來儲存參與 Windows Sockets 通訊的電腦之 Internet Protocol \(IP\) 位址。  
  
## 語法  
  
```  
  
      struct sockaddr {  
   unsigned short sa_family;  
   char sa_data[14];  
};  
```  
  
#### 參數  
 *sa\_family*  
 通訊端通訊協定家族。  
  
 *sa\_data*  
 所有不同的通訊端位址最大值結構。  
  
## 備註  
 Microsoft TCP\/IP 通訊端開發人員的套件只支援網際網路位址網域。  要實際填入地址的每個部分的值，請使用 `SOCKADDR_IN` 資料結構，是特別為這個位址的格式。  `SOCKADDR` 和 `SOCKADDR_IN` 資料結構有相同的大小。  您簡易地切換兩個結構型別。  
  
## 需求  
 **標頭：**winsock2.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR\_IN 結構](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)   
 [CSocket::Create](../Topic/CSocket::Create.md)