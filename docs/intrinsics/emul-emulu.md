---
title: "__emul、__emulu | Microsoft Docs"
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
  - "__emulu_cpp"
  - "__emul"
  - "__emul_cpp"
  - "__emulu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 __emul"
  - "內建 __emulu"
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __emul、__emulu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 執行可保留的 32 位元整數的溢位的乘積。  
  
## 語法  
  
```  
__int64 __emul(  
   int a,  
   int b  
);  
unsigned __int64 __emulu(  
   unsigned int a,  
   unsigned int b  
);  
```  
  
#### 參數  
 \[in\] `a`  
 第一個整數運算元的乘法運算。  
  
 \[in\] `b`  
 第二個整數運算元的乘法運算。  
  
## 傳回值  
 乘法運算的結果。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__emul`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__emulu`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `__emul`兩個 32 位元帶正負號的值，然後傳回做為 64 位元帶正負號的整數值相乘的結果。  
  
 `__emulu`兩個 32 位元不帶正負號的整數值，然後傳回做為 64 位元不帶正負號的整數值相乘的結果。  
  
## 範例  
  
```  
// emul.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__emul)  
#pragma intrinsic(__emulu)  
  
int main()  
{  
   int a = -268435456;   
   int b = 2;   
  
   __int64 result = __emul(a, b);  
  
   cout << a << " * " << b << " = " << result << endl;  
  
   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295  
   unsigned int ub = 0xF000000;  // Dec value: 251658240  
  
   unsigned __int64 uresult = __emulu(ua, ub);  
  
   cout << ua << " * " << ub << " = " << uresult << endl;  
  
}  
```  
  
## Output  
  
```  
-268435456 * 2 = -536870912  
4294967295 * 251658240 = 1080863910317260800  
```  
  
### 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)