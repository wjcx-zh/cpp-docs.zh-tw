---
title: "float_control | Microsoft Docs"
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
  - "vc-pragma.float_control"
  - "float_control_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "float_control pragma"
  - "Pragma, float_control"
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: 11
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# float_control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定函式的浮點行為。  
  
## 語法  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## 旗標  
 `value` *,* `setting` **\[push\]**  
 指定浮點行為。  `value` 可以是 **precise**  或 **except**。  如需詳細資訊，請參閱 [\/fp \(指定浮點數行為\)](../build/reference/fp-specify-floating-point-behavior.md)。  `setting` 可以是 **on**  或 **off**。  
  
 如果 `value` 為 **precise**，則會指定 **precise** 和 **except** 的設定。  當 **precise**  也設定為 **on** 時，**except** 只能設定為 **on** 。  
  
 如果新增了選擇性的 **push** 語彙基元，則會將 `value` 的目前設定推入至內部編譯器堆疊。  
  
 **push**  
 將目前的 `float_control` 設定推入至內部編譯器堆疊。  
  
 **pop**  
 從內部編譯器堆疊的頂端移除`float_control` 設定，並建立新的 `float_control` 設定。  
  
## 備註  
 當 **except** 開啟時，您便無法將 `float_control precise` 關閉。  同樣地，當 `fenv_access` 開啟時，便無法關閉 **precise**。  若要使用 `float_control` pragma 從 strict 模型移至 fast 模型，請使用下列程式碼：  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
// The following line is needed on Itanium processors  
#pragma fp_contract(on)  
```  
  
 若要使用 `float_control` pragma 從 fast 模型移至 strict 模型，請使用下列程式碼：  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
// The following line is needed on Itanium processors.  
#pragma fp_contract(off)  
```  
  
 其他浮點 pragma 包括：  
  
-   [fenv\_access](../preprocessor/fenv-access.md)  
  
-   [fp\_contract](../preprocessor/fp-contract.md)  
  
## 範例  
 下列範例顯示如何使用 pragma `float_control` 攔截溢位浮點例外狀況。  
  
```  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
  **成功**   
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)