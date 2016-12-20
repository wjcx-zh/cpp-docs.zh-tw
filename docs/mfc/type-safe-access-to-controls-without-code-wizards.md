---
title: "不使用程式碼精靈的控制項類型安全存取 | Microsoft Docs"
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
  - "對話方塊控制項, 存取"
  - "對話方塊, 存取控制項"
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 不使用程式碼精靈的控制項類型安全存取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要建立的型別安全存取的第一個方法對控制項使用內嵌成員函式轉換為類別 `CWnd` `GetDlgItem` 成員函式的傳回型別變更為適當的 C\+\+ 控制項型別，如下列範例所示:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/CPP/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 您可以使用這個成員函式存取控制以與程式碼的型別安全方式如下所示:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/CPP/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## 請參閱  
 [對話方塊中之控制項的類型安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [使用程式碼精靈的控制項類型安全存取](../mfc/type-safe-access-to-controls-with-code-wizards.md)