---
title: "HTTP 的基本概念 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67921e0667267b99b3787d55fa7ff564aa543ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="http-basics"></a>HTTP 的基本概念
撰寫網際網路應用程式時，通常會檢查並在 HTTP 標頭中加入資訊。 傳回碼表示所要求的事件為成功或失敗。 下表中列出數個常用的傳回碼。  
  
|傳回碼|意義|  
|-----------------|-------------|  
|200|找到 URL，接著進行傳輸|  
|400|難以理解的要求|  
|404|找不到要求的 URL|  
|405|伺服器不支援所要求的方法|  
|500|未知的伺服器錯誤|  
|503|服務無法使用|  
  
 下列表格中顯示各組 HTTP 回應。  
  
|群組|意義|  
|-----------|-------------|  
|200-299|成功|  
|300-399|資訊|  
|400-499|要求錯誤|  
|500-599|伺服器錯誤|  
  
 超文字傳輸通訊協定 (HTTP) 是超媒體資訊系統的一種應用層通訊協定。 如需 HTTP 的詳細資訊，請參閱 Web 瀏覽器和伺服器的通訊方式，以及參閱超文字傳輸通訊協定 (HTTP) 規格：  
  
 [http://www.w3.org/pub/WWW/Protocols/](http://www.w3.org/pub/www/protocols/)  
  
## <a name="see-also"></a>請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)

