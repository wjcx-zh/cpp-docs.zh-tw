---
title: ".Exp 檔做為連結器輸入 | Microsoft Docs"
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
  - ".exp 檔案 [C++]"
  - "EXP 檔案"
  - "匯出資料, 匯出 (.exp) 檔案"
  - "匯出函式"
  - "匯出函式, 有關匯出函式的資訊"
  - "函式 [C++], 匯出"
  - "匯入程式庫, 連結器檔案"
  - "連結 [C++], 匯出"
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Exp 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

匯出檔 \(.exp\)  含有關於匯出函式 \(Exported Function\) 及資料項目的資訊。  當 LIB 建立匯入程式庫時，它也會建立一個 .exp 檔。  當您要連結一個同時要對另一個程式匯出及匯入 \(不論是直接或間接\) 的程式時，您必須使用 .exp 檔。  如果您以 .exp 檔案連結，LINK 不會產生匯入程式庫，因為它會假設 LIB 已經建立了一個。  如需有關 .exp 檔及匯入程式庫的詳細資訊，請參閱[使用匯入程式庫和匯出檔案](../../build/reference/working-with-import-libraries-and-export-files.md)。  
  
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)