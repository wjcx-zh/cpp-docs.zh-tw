---
title: "如何：在狀態列中顯示命令資訊 | Microsoft Docs"
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
  - "顯示命令狀態"
  - "提示 [C++]"
  - "狀態列, 顯示命令資訊"
  - "狀態列, 訊息區域"
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：在狀態列中顯示命令資訊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您執行應用程式精靈建立應用程式的基本架構時，您可以支援工具列和狀態列。  在應用程式精靈中的選項支援兩個。  當狀態列存在時，應用程式會自動提供有用的意見，當使用者將游標移至項目的指標位於功能表。  表示功能表項目反白顯示時，應用程式會自動顯示在狀態列的提示字串。  例如，在中，當使用者將游標移至 \[**剪下**\] 命令的指標位於 \[**編輯**\] 功能表時，狀態列會顯示「剪下選取並將它放在剪貼簿」在狀態列中的訊息區。  這個提示以協助使用者了解功能表項目的用途。  當使用者按一下工具列按鈕，這也運作。  
  
 您可以定義一個功能表項目的提示字串可以新增至這個狀態列協助您新增至程式。  當您編輯功能表項目的屬性在功能表編輯器時，要這樣做，請提供提示字串。  您定義的字串在應用程式資源檔中儲存;它們與命令它們解譯的 ID。  
  
 根據預設，應用程式精靈加入 `AFX_IDS_IDLEMESSAGE`，標準的 ID 就緒訊息，顯示，當程式等待新訊息時。  如果您在應用程式精靈指定即時線上說明選項，訊息變更為「為說明，按 F1」。  
  
## 請參閱  
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)