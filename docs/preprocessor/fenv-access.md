---
title: "fenv_access | Microsoft Docs"
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
  - "vc-pragma.fenv_access"
  - "fenv_access_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fenv_access pragma"
  - "Pragma, fenv_access"
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fenv_access
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

停用 \(ON\) 或啟用 \(OFF\) 可變更旗標測試和模式變更的最佳化。  
  
## 語法  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## 備註  
 根據預設，`fenv_access` 為 OFF。  
  
 如需浮點行為的詳細資訊，請參閱 [\/fp \(指定浮點數行為\)](../build/reference/fp-specify-floating-point-behavior.md)。  
  
 受限於 `fenv_access` 的最佳化類型包括：  
  
-   全域通用子運算式刪除  
  
-   程式碼移動  
  
-   常數摺疊  
  
 其他浮點 pragma 包括：  
  
-   [float\_control](../preprocessor/float-control.md)  
  
-   [fp\_contract](../preprocessor/fp-contract.md)  
  
## 範例  
  
```  
// pragma_directive_fenv_access_x86.cpp  
// compile with: /O2  
// processor: x86  
#include <stdio.h>  
#include <float.h>   
#include <errno.h>  
#pragma fenv_access (on)  
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
  **out\=9.999999776482582e\-003**   
## 範例  
 下列範例是產生 Itanium 處理器輸出檔的編譯器。  **\/fp:precise** 會以擴充精確度保留中繼結果，這樣就可計算大於 FLT\_MAX \(3.402823466e\+38F\) 的值，而該總和將產生 1.0 的結果 \(應與手動計算的結果相同\)。  **\/fp:strict** 會以其原始精確度 \(浮點\) 保留中繼結果，如此第一個加法會產生無限大的結果，並且保留在運算式中。  
  
```  
// pragma_directive_fenv_access_IPF.cpp  
// compile with: /O2 /fp:precise  
// processor: IPF  
// compiling with /fp:precise prints 1.0F  
// compile with /fp:strict to print infinity  
  
#include <stdio.h>  
float arr[5] = {3.402823465e+38F,   
               3.402823462e+38F,  
               3.402823464e+38F,  
               3.402823463e+38F,  
               1.0F};  
  
int main() {  
   float sum = 0;  
   sum = arr[0] + arr[1] - arr[2] - arr[3] + arr[4];  
   printf_s("%f\n", sum);  
}  
```  
  
  **1.000000**   
## 範例  
 從先前的範例將 `#pragma fenv_access (on)` 標記為註解時請注意，輸出會有所不同，因為編譯器會進行編譯時期求值，而不會使用控制模式。  
  
```  
// pragma_directive_fenv_access_2.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>   
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
  **out\=1.000000000000000e\-002**   
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)