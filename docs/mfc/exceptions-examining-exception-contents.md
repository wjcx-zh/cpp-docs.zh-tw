---
title: "例外狀況：檢查例外狀況內容 | Microsoft Docs"
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
  - "catch 區塊, MFC 函式例外狀況"
  - "CException 類別, 類別例外狀況"
  - "例外狀況處理, MFC"
  - "擲回例外狀況, 例外狀況內容"
  - "try-catch 例外狀況處理, 例外狀況內容"
  - "try-catch 例外狀況處理, MFC 函式例外狀況"
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況：檢查例外狀況內容
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

雖然 catch 區塊的引數可以幾乎任何資料型別， MFC 函式擲回衍生自類別之型別的例外狀況的 `CException`。  若要攔截 MFC 函式所擲回的例外狀況，然後，您可以撰寫引數是指向 `CException` 物件的 catch 區塊 \(或衍生自 `CException`的物件，例如 `CMemoryException`\)。  根據例外狀況的確切型別，您可以檢查例外狀況物件的資料成員對彙總資訊的有關例外狀況的特定原因。  
  
 例如， `CFileException` 型別的 `m_cause` 資料成員，會包含列舉型別指定此案例外的原因。  可能的傳回值的範例是 **CFileException::fileNotFound** 和 **CFileException::readOnly**。  
  
 下列範例顯示如何檢查 `CFileException`的內容。  其他例外狀況型別可以相同方式檢查。  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/CPP/exceptions-examining-exception-contents_1.cpp)]  
  
 如需詳細資訊，請參閱 [例外狀況:在例外狀況的釋放物件](../mfc/exceptions-freeing-objects-in-exceptions.md) 和 [例外狀況:攔截和刪除例外狀況。](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)