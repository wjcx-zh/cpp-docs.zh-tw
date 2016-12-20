---
title: ".PUSHREG | Microsoft Docs"
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
  - ".PUSHREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".PUSHREG directive"
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .PUSHREG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會產生`UWOP_PUSH_NONVOL`回溯程式碼項目，針對指定的暫存器使用目前的初構中位移的號碼。  
  
## 語法  
  
```  
.PUSHREG register  
```  
  
## 備註  
 .PUSHREG 允許 ml64.exe 洏峈會指定如何框架函式回溯時，以及只允許在初構中，從延伸[PROC](../../assembler/masm/proc.md)框架宣告，以[.ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  這些指示詞並不會產生程式碼路徑。 它們只會產生`.xdata`和`.pdata`。  .PUSHREG 前面必須有實際實作卸載動作的指示進行。  它是很好的作法，以包裝回溯指示詞，並將程式碼是在巨集中的回溯可確保合約。  
  
 如需詳細資訊，請參閱 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 範例  
  
### 描述  
 下列範例會示範如何將推入靜態 tegisters。  
  
### 程式碼  
  
```  
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
Example1 PROC FRAME  
   push r10  
.pushreg r10  
   push r15  
.pushreg r15  
   push rbx  
.pushreg rbx  
   push rsi  
.pushreg rsi  
.endprolog  
   ; rest of function ...  
   ret  
Example1 ENDP  
_text ENDS  
END  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)