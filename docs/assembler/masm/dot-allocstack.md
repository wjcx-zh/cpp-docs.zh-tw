---
title: ".ALLOCSTACK | Microsoft Docs"
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
  - ".ALLOCSTACK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ALLOCSTACK directive"
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .ALLOCSTACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會產生 **UWOP\_ALLOC\_SMALL** 或 **UWOP\_ALLOC\_LARGE** 以指定的大小，目前在初構中位移。  
  
## 語法  
  
```  
.ALLOCSTACK size  
```  
  
## 備註  
 MASM 都可以選擇指定的大小最有效率的編碼方式。  
  
 .ALLOCSTACK 允許 ml64.exe 洏峈指定框架的函式的回溯，並只允許在初構中，從延伸[程序](../../assembler/masm/proc.md) 框架宣告，以  [。ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指示詞。  這些指示詞並不會產生程式碼路徑。 它們只會產生`.xdata`和`.pdata`。  .ALLOCSTACK 前面必須有實際實作卸載動作的指示進行。  它是很好的作法，以包裝回溯指示詞，並將程式碼是在巨集中的回溯可確保合約。  
  
 `size`的運算元必須是 8 的倍數。  
  
 如需詳細資訊，請參閱 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 範例  
 下列範例會示範如何以指定的例外狀況回溯\/處理常式：  
  
```  
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console  
text SEGMENT  
PUBLIC Example3  
PUBLIC Example3_UW  
Example3_UW PROC NEAR  
   ; exception/unwind handler body  
  
   ret 0  
  
Example3_UW ENDP  
  
Example3 PROC FRAME : Example3_UW  
  
   sub rsp, 16  
.allocstack 16  
  
.endprolog  
  
   ; function body  
    add rsp, 16  
   ret 0  
  
Example3 ENDP  
text ENDS  
END  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)