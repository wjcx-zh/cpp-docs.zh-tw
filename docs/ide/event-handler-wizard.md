---
title: "事件處理常式精靈 | Microsoft Docs"
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
  - "vc.codewiz.eventhandler.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件處理常式精靈 [C++]"
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 事件處理常式精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈會將對話方塊控制項的事件處理常式加入至您選取的類別。  如果您從[屬性視窗](../Topic/Properties%20Window.md)加入事件處理常式，只可以將它加入至實作對話方塊的類別。  如需詳細資訊，請參閱[加入對話方塊控制項的事件處理常式](../mfc/adding-event-handlers-for-dialog-box-controls.md)。  
  
 **命令名稱**  
 識別要加入事件處理常式的選取控制項。  此方塊無法使用。  
  
 **訊息類型**  
 顯示選取的控制項目前可能使用的訊息處理常式清單。  
  
 **函式處理常式名稱**  
 顯示為了處理事件而加入的函式名稱。  根據預設，名稱會根據訊息類型和命令而定，並於前端加上 "On"。  例如，對一個名為 `IDC_BUTTON1` 的按鈕，`BN_CLICKED` 訊息類型會顯示 `OnBnClickedButton1` 函式處理常式名稱。  
  
 **類別清單**  
 顯示您可以加入事件處理常式的可用類別。  選取的對話方塊類別會以紅色顯示。  
  
 **處理常式描述**  
 提供於 \[訊息類型\] 方塊中選取項目的描述。  此方塊無法使用。  
  
 **加入並編輯**  
 將訊息處理常式加入至選取的類別或物件，然後將新增的函式以文字編輯器開啟以加入控制項告知處理常式程式碼。  
  
 **編輯程式碼**  
 將選取的現有函式以文字編輯器開啟，讓您可以加入和編輯控制項告知處理常式程式碼。  
  
## 請參閱  
 [加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)