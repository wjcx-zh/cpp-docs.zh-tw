---
title: "PROC | Microsoft Docs"
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
  - "PROC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROC directive"
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# PROC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫程序區塊的開始與結束標記*標籤*。  在區塊中的陳述式也可以呼叫**呼叫** 指令或 [叫用](../../assembler/masm/invoke.md)指示詞。  
  
## 語法  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## 備註  
 框架 \[：*ehandler 位址*\] 只有不適用於 ml64.exe，且會導致 MASM 產生函式表項目中的.pdata 和回溯資訊在.xdata 中的函式的結構化例外處理的回溯行為。  
  
 當**框架**屬性，則必須跟隨著[.ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  
  
 請參閱[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)如需有關使用 ml64.exe。  
  
## 範例  
  
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
  
 上述程式碼會發出下列函式表，並回溯資訊：  
  
```  
FileHeader->Machine 34404  
Dumping Unwind Information for file ex2.exe  
  
.pdata entry 1 0x00001000 0x00001023  
  
  Unwind data: 0x00002000  
  
    Unwind version: 1  
    Unwind Flags: None  
    Size of prologue: 0x08  
    Count of codes: 3  
    Frame register: rbp  
    Frame offset: 0x0  
    Unwind codes:  
  
      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00  
      Code offset: 0x05, ALLOC_SMALL, size=0x10  
      Code offset: 0x01, PUSH_NONVOL, register=rbp  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)