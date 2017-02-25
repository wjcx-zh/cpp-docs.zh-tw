---
title: "fp_contract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.fp_contract"
  - "fp_contract_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fp_contract pragma"
  - "Pragma, fp_contract"
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# fp_contract
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

決定是否會發生浮點縮減。  
  
## 語法  
  
```  
#pragma fp_contract [ON | OFF]  
```  
  
## 備註  
 `fp_contract` 依預設為開啟。  
  
 如需浮點行為的詳細資訊，請參閱 [\/fp \(指定浮點數行為\)](../build/reference/fp-specify-floating-point-behavior.md)。  
  
 其他浮點 pragma 包括：  
  
-   [fenv\_access](../preprocessor/fenv-access.md)  
  
-   [float\_control](../preprocessor/float-control.md)  
  
## 範例  
 這個範例產生的程式碼不會使用在 Itanium 處理器的融合乘積和 \(**fma**\) 指示。  如果您將 `#pragma fp_contract (off)` 標記為註解，產生的程式碼會使用 **fma** 指示。  
  
```  
// pragma_directive_fp_contract.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>  
  
#pragma fp_contract (off)   
  
int main() {  
   double z, b, t;  
  
   for (int i = 0; i < 10; i++) {  
      b = i * 5.5;  
      t = i * 56.025;  
      _set_controlfp(_PC_24, _MCW_PC);  
  
      z = t * i + b;  
      printf_s ("out=%.15e\n", z);  
   }  
}  
```  
  
  **out\=0.000000000000000e\+000**  
**out\=6.152500152587891e\+001**  
**out\=2.351000061035156e\+002**  
**out\=5.207249755859375e\+002**  
**out\=9.184000244140625e\+002**  
**out\=1.428125000000000e\+003**  
**out\=2.049899902343750e\+003**  
**out\=2.783724853515625e\+003**  
**out\=3.629600097656250e\+003**  
**out\=4.587524902343750e\+003**   
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)