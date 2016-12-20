---
title: "例外狀況處理常式的限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "例外狀況處理, 例外狀況處理常式"
  - "限制, 例外狀況處理常式"
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況處理常式的限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在程式碼中使用例外狀況處理常式的主要限制是，您不能使用 `goto` 陳述式跳入 `__try` 陳述式區塊。  您必須改為透過一般控制流程進入陳述式區塊。  您可以跳出 `__try` 陳述式區塊，並且依您選擇的方式將例外狀況處理常式巢狀化。  
  
## 請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)