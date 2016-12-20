---
title: "哪裡可以找到訊息對應 | Microsoft Docs"
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
  - "尋找訊息對應"
  - "巨集, 訊息對應"
  - "訊息對應, 尋找"
  - "訊息對應巨集"
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 哪裡可以找到訊息對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用應用程式精靈中建立新的基本架構應用程式，應用程式會為每個命令目標類別寫入它為您建立的訊息對應。  這包括您的衍生的應用程式、文件、檢視和框架視窗類別。  這些訊息對應已經有某些訊息的應用程式精靈提供的輸入並預先定義命令，，有些則是您要加入的處理常式的預留位置。  
  
 類別的訊息對應位於類別的 .CPP 檔案。  使用應用程式精靈建立的基本訊息對應時，您使用屬性視窗將訊息的輸入和命令的類別處理。  將某些項目後，典型的訊息對應可能如下所示:  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/CPP/where-to-find-message-maps_1.cpp)]  
  
 訊息對應包含巨集的集合。  兩個巨集， [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 和 [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md)，例如訊息對應。  其他巨集，例如 `ON_COMMAND`，填入訊息對應的內容。  
  
> [!NOTE]
>  訊息對應巨集不會由分號後面。  
  
 當您使用加入類別精靈建立新的類別時，它會提供類別的訊息對應。  或者，使用原始程式碼編輯器中，您可以手動建立訊息對應。  
  
## 請參閱  
 [架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)