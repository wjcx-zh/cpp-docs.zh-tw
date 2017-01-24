---
title: "使用內嵌組譯碼撰寫函式 | Microsoft Docs"
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
  - "__asm 關鍵字 [C++], 在函式中"
  - "組譯工具 [C++], 撰寫函式"
  - "函式 [C++], 內嵌組譯碼"
  - "內嵌組譯碼 [C++], 撰寫函式"
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用內嵌組譯碼撰寫函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 如果您撰寫內嵌組譯程式碼的函式，很容易將引數傳遞至函式，並從其傳回值。  下列範例會比較第一次針對不同的組譯工具寫，然後重寫為內嵌組譯工具的函式。  呼叫的函式 `power2`，會收到兩個參數，乘以 2 的乘冪第二個參數中的第一個參數。  撰寫為分開的組譯工具，函式看起來可能像這樣：  
  
```  
; POWER.ASM  
; Compute the power of an integer  
;  
       PUBLIC _power2  
_TEXT SEGMENT WORD PUBLIC 'CODE'  
_power2 PROC  
  
        push ebp        ; Save EBP  
        mov ebp, esp    ; Move ESP into EBP so we can refer  
                        ;   to arguments on the stack  
        mov eax, [ebp+4] ; Get first argument  
        mov ecx, [ebp+6] ; Get second argument  
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )  
        pop ebp         ; Restore EBP  
        ret             ; Return with sum in EAX  
  
_power2 ENDP  
_TEXT   ENDS  
        END  
```  
  
 由於它針對個別的組譯工具撰寫，函式會要求不同的來源檔案和組件與連結步驟。  C 和 c \+ \+ 函式引數通常使用在堆疊上，所以此版本的`power2`函式存取它的引數，依其在堆疊上的位置。  \(請注意， **模型**指示詞，可用於 MASM 和一些其他的組合，也可以讓您依名稱存取堆疊引數和本機堆疊變數。\)  
  
## 範例  
 這個程式寫入`power2`內嵌組譯程式碼的函式：  
  
```  
// Power2_inline_asm.c  
// compile with: /EHsc  
// processor: x86  
  
#include <stdio.h>  
  
int power2( int num, int power );  
  
int main( void )  
{  
    printf_s( "3 times 2 to the power of 5 is %d\n", \  
              power2( 3, 5) );  
}  
int power2( int num, int power )  
{  
   __asm  
   {  
      mov eax, num    ; Get first argument  
      mov ecx, power  ; Get second argument  
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )  
   }  
   // Return with result in EAX  
}  
```  
  
 內嵌版本`power2`函式依名稱參照它的引數，並會出現在其他程式時相同的原始程式檔。  這個版本也需要較少的組譯碼指令。  
  
 因為內嵌版本`power2`不會執行 C  `return`陳述式，它會無害的警告如果您編譯在警告層級 2 或更高。  函式不會傳回一個值，但是編譯器無法分辨，缺乏`return`陳述式。  您可以使用 [\#pragma 警告](../../preprocessor/warning.md)來停用這項警告的產生。  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)