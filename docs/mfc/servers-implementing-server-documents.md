---
title: "伺服器：實作伺服器文件 | Microsoft Docs"
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
  - "OLE 伺服器應用程式, 實作 OLE 伺服器"
  - "OLE 伺服器應用程式, 管理伺服器文件"
  - "伺服器文件, 實作"
  - "伺服器, 伺服器文件"
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 伺服器：實作伺服器文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明您必須採取成功實作伺服器資料的步驟，如果您在應用程式精靈沒有指定 OLE 伺服器選項。  
  
#### 定義伺服器資料類別  
  
1.  從 `COleServerDoc` 衍生您自己的文件類別而非 **CDocument**。  
  
2.  建立衍生自 `COleServerItem`的伺服器項目類別。  
  
3.  實作您的伺服器資料類別的 `OnGetEmbeddedItem` 成員函式。  
  
     當容器應用程式的使用者建立或編輯內嵌項目時，呼叫`OnGetEmbeddedItem` 。  它會傳回代表整份文件的項目。  這應該為 `COleServerItem`物件衍生類別。  
  
4.  覆寫 `Serialize` 成員函式序列化文件的內容。  除非您使用它們代表您的文件上，原生資料時不需要序列化伺服器項目清單。  如需詳細資訊，請參閱文件 [伺服器:伺服器項目](../mfc/servers-server-items.md)上 *實作伺服器項目* 。  
  
 當伺服器文件時，架構會自動向這個 OLE 系統 DLL 的文件。  這可讓 DLL 識別伺服器文件。  
  
 在 *類別庫參考 \(*如需詳細資訊，請參閱 [COleServerItem](../mfc/reference/coleserveritem-class.md) 和 [COleServerDoc](../mfc/reference/coleserverdoc-class.md) 。  
  
## 請參閱  
 [伺服器](../mfc/servers.md)   
 [伺服器：伺服器項目](../mfc/servers-server-items.md)   
 [伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)   
 [伺服器：實作就地編輯框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)