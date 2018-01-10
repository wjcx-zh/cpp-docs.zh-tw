---
title: "使用內嵌組譯碼撰寫函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2fc9e6a1d2c94e74ef8aabf085af8fc4dc0bc28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="writing-functions-with-inline-assembly"></a>使用內嵌組譯碼撰寫函式
## <a name="microsoft-specific"></a>Microsoft 特定的  
 如果您撰寫具有內嵌組譯程式碼的函式，很容易就能將引數傳遞至函式，並從函式傳回值。 下列範例將比較原先針對另一個組合語言撰寫，後來針對內嵌組合語言重寫的函式。 稱為 `power2` 的函式會收到兩個參數，並將第一個參數乘以 2 得到第二個參數的乘冪。 針對另一個組合語言撰寫的函式外觀會像這樣：  
  
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
  
 由於函式是針對另一個組合語言所撰寫，因此需要另一個原始程式檔以及組譯碼和連結步驟。 C 和 C++ 函式引數通常會在堆疊上傳遞，因此這個版本的 `power2` 函式會依據它們在堆疊上的位置存取其引數  (請注意，**模型**指示詞，可在 MASM 和其他組合語言，也可讓您依名稱存取堆疊引數和本機堆疊變數。)  
  
## <a name="example"></a>範例  
 這個程式會使用內嵌組譯程式碼撰寫 `power2` 函式：  
  
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
  
 `power2` 函式的內嵌版本會依名稱參考其引數，並且與程式的其他部分出現在相同的原始程式檔。 這個版本需要的組譯碼指令也比較少。  
  
 由於 `power2` 的內嵌版本不會執行 C `return` 陳述式，如果您是在警告層級 2 (含) 更高層級進行編譯，它就會產生無害的警告。 函式確實會傳回值，不過，編譯器在沒有 `return` 陳述式時無法分辨這種情形。 您可以使用[#pragma 警告](../../preprocessor/warning.md)停用產生這個警告。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)