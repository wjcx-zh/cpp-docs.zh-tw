---
title: "HTTP 的基本概念 | Microsoft Docs"
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
  - "HTTP 要求, 傳回碼"
  - "HTTP, 傳回碼"
  - "傳回碼"
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# HTTP 的基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當撰寫網際網路應用程式時，通常會檢查和加入 HTTP 標頭資訊。  傳回碼表示要求的事件是成功或失敗。  數個常用傳回碼在下表中列出。  
  
|傳回碼|意義|  
|---------|--------|  
|200|URL 定位，接著傳輸|  
|400|難以理解的要求|  
|404|找不到要求的 URL|  
|405|伺服器不支援要求的方法|  
|500|未知的伺服器錯誤。|  
|503|服務無法使用|  
  
 HTTP 回應分組顯示於下列表格中。  
  
|群組|意義|  
|--------|--------|  
|200–299|成功|  
|300–399|資訊|  
|400–499|要求錯誤|  
|500–599|伺服器錯誤|  
  
 超文字傳輸通訊協定 \(HTTP\) 大於媒體資訊系統的應用程式層級通訊協定。  如需 HTTP 的詳細資訊，請參閱和 Web 瀏覽器和伺服器的通訊方式，及參閱超文字傳輸通訊協定 \(HTTP\) 規格：  
  
 [http:\/\/www.w3.org\/pub\/WWW\/Protocols\/](http://www.w3.org/pub/WWW/Protocols/)  
  
## 請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)