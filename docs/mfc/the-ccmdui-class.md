---
title: "CCmdUI 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdUI 類別, 功能表更新"
  - "工具列 [C++], 更新"
  - "更新處理常式"
  - "更新使用者介面物件"
  - "使用者介面物件, 更新"
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CCmdUI 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當傳送更新命令至其處理常式時，此架構會處理常式指標至 `CCmdUI` 物件 \(或對 `CCmdUI`物件的衍生類別\)。  這個物件代表產生命令的功能表項目或工具列按鈕或其他使用者介面物件。  更新處理常式是經由指標呼叫 `CCmdUI` 結構的成員函式來更新使用者介面物件。  例如，這是新的更新處理常式所有功能表項目:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/CPP/the-ccmdui-class_1.cpp)]  
  
 這個處理常式呼叫的物件的 **Enable** 成員函式與存取功能表項目。  **Enable** 做項目可供使用。  
  
## 請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)