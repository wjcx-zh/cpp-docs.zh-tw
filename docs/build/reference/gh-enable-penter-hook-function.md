---
title: "/Gh (啟用 _penter 攔截函式) | Microsoft Docs"
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
  - "_penter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gh 編譯器選項 [C++]"
  - "_penter 函式"
  - "Gh 編譯器選項 [C++]"
  - "-Gh 編譯器選項 [C++]"
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gh (啟用 _penter 攔截函式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使得每個方法或函式開始時，都會呼叫 `_penter` 函式。  
  
## 語法  
  
```  
/Gh  
```  
  
## 備註  
 `_penter` 函式並非任何程式庫的一部分，必須由您來提供 `_penter` 的定義。  
  
 除非您打算明確地呼叫 `_penter`，否則您不需要提供原型。  這個函式必須如同擁有下列原型一樣地出現，而且它必須在進入時推入所有暫存器的內容並且在離開時取出未變更的內容：  
  
```  
void __declspec(naked) _cdecl _penter( void );  
```  
  
 這個宣告不適用於 64 位元專案。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 範例  
 下列程式碼在使用 **\/Gh** 編譯時，會顯示如何兩次呼叫 `_penter`；一次是在進入函式 `main` 時，另一次是在進入函式 `x` 時。  
  
```  
// Gh_compiler_option.cpp  
// compile with: /Gh  
// processor: x86  
#include <stdio.h>  
void x() {}  
  
int main() {  
   x();  
}  
  
extern "C" void __declspec(naked) _cdecl _penter( void ) {  
   _asm {  
      push eax  
      push ebx  
      push ecx  
      push edx  
      push ebp  
      push edi  
      push esi  
    }  
  
   printf_s("\nIn a function!");  
  
   _asm {  
      pop esi  
      pop edi  
      pop ebp  
      pop edx  
      pop ecx  
      pop ebx  
      pop eax  
      ret  
    }  
}  
```  
  
  **在函式中！**  
**在函式中！**   
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)