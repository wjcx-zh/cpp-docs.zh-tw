---
title: ".PUSHFRAME | Microsoft Docs"
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
  - ".PUSHFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".PUSHFRAME directive"
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .PUSHFRAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會產生`UWOP_PUSH_MACHFRAME`回溯程式碼項目。  如果選擇性`code`指定，則回溯程式碼項目會指定為 1 的修飾詞。  否則修飾詞為 0。  
  
## 語法  
  
```  
.PUSHFRAME [code]  
```  
  
## 備註  
 .PUSHFRAME 允許 ml64.exe 洏峈指定框架的函式的回溯，並只允許在初構中，從延伸[PROC](../../assembler/masm/proc.md)框架宣告，以[.ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  這些指示詞並不會產生程式碼路徑。 它們只會產生`.xdata`和`.pdata`。  .PUSHFRAME 前面必須有實際實作卸載動作的指示進行。  它是很好的作法，以包裝回溯指示詞，並將程式碼是在巨集中的回溯可確保合約。  
  
 如需詳細資訊，請參閱 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)