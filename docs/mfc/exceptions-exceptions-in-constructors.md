---
title: "例外狀況：建構函式中的例外狀況 | Microsoft Docs"
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
  - "建構函式 [C++], 例外狀況"
  - "例外狀況, 在建構函式中"
  - "擲回例外狀況, 在建構函式中"
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況：建構函式中的例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當在建構函式中擲回例外狀況，請清除在擲回例外狀況之前配置的任何物件和記憶體配置，如 [例外狀況:從您的函式中擲回例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)所說明。  
  
 當在建構函式中擲回例外狀況，建構函式呼叫的時機已經配置物件的記憶體。  因此，在這種情況下，擲回例外狀況之後，編譯器會自動解除配置物件所佔用的記憶體。  
  
 如需詳細資訊，請參閱 [例外狀況:在例外狀況的釋放物件](../mfc/exceptions-freeing-objects-in-exceptions.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)