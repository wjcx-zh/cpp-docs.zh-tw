---
title: "SOCKADDR_IN 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SOCKADDR_IN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SOCKADDR_IN 結構"
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# SOCKADDR_IN 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在網際網路位址家族中，Windows Sockets 使用 `SOCKADDR_IN` 結構來指定與通訊端連接的本機或遠端端點位址。  
  
## 語法  
  
```  
  
      struct sockaddr_in{  
   short sin_family;  
   unsigned short sin_port;  
   struct in_addr sin_addr;  
   char sin_zero[8];  
};  
```  
  
#### 參數  
 *sin\_family*  
 位址家族 \(必須是 **AF\_INET**\)。  
  
 *sin\_port*  
 IP 通訊埠。  
  
 *sin\_addr*  
 IP 位址。  
  
 *sin\_zero*  
 用來讓結構和 `SOCKADDR` 的大小相同的填補。  
  
## 備註  
 這是網際網路位址家族特定的 `SOCKADDR` 結構形式，而且可以轉型為 `SOCKADDR`。  
  
 這個結構的 IP 位址元件是類型 **IN\_ADDR**。  **IN\_ADDR** 結構在 Windows Sockets 標頭檔 WINSOCK.H 中定義如下：  
  
 `struct   in_addr {`  
  
 `union   {`  
  
 `struct{`  
  
 `unsigned  char   s_b1,`  
  
 `s_b2,`  
  
 `s_b3,`  
  
 `s_b4;`  
  
 `}  S_un_b;`  
  
 `struct  {`  
  
 `unsigned  short  s_w1,`  
  
 `s_w2;`  
  
 `}  S_un_w;`  
  
 `unsigned long  S_addr;`  
  
 `} S_un;`  
  
 `};`  
  
## 需求  
 **標頭：**winsock2.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR 結構](../../mfc/reference/sockaddr-structure.md)