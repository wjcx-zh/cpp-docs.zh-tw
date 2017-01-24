---
title: "參數傳遞 | Microsoft Docs"
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
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 參數傳遞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

前四個整數引數在暫存器中傳遞。  整數值會在 RCX、RDX、R8 和 R9 傳遞 \(順序由左至右的\)。  引數五個 \(含\) 以上堆疊上傳遞。  所有引數是靠右對齊在暫存器。  因為會執行這項動作，所以被呼叫端可以在需要時忽略暫存器中較高的位元，並且只存取所需之暫存器的部分。  
  
 浮點數和雙精度引數會在 XMM0 到 XMM3 \(最多 4 個\) 中傳遞，而整數位置 \(RCX、RDX、R8 和 R9\) 則通常用來做為會忽略的基數位置 \(請參閱範例\)，反之亦然。  
  
 [\_\_m128](../cpp/m128.md) 型別、陣列和字串永遠不會立即值，但是指標能透過所配置的記憶體中的呼叫端。  大小為 8， 16， 32 個或 64 個位元和 \_\_m64 結構\/等位會傳遞，就如同它們是相同大小的整數。  結構\/等位會刪除這些大小之外傳遞為指標所配置的記憶體中的呼叫端。  對於這些傳遞為指標 \(包括 \_\_m128\) 的彙總 \(Aggregate\) 型別，呼叫端配置的暫存記憶體會對齊 16 位元組。  
  
 不配置堆疊空間而且不呼叫其他函式的內建函式，可以使用其他動態暫存器以傳遞額外的暫存器引數，因為編譯器 \(Compiler\) 和內建函式實作 \(Implementation\) 之間有緊密的繫結。  這是進一步改善效能的機會。  
  
 被呼叫端要負責視需要將暫存器參數傾印至其遮蔽空間。  
  
 下表會摘要說明參數傳遞的方式：  
  
|參數型別|如何傳遞|  
|----------|----------|  
|浮點數|前 4 個參數 – XMM0 到 XMM3。  其他的會透過堆疊傳遞。|  
|Integer|前 4 個參數 – RCX、RDX、R8、R9。  其他的會透過堆疊傳遞。|  
|彙總 \(8、16、32 or 64 位元\) 和 \_\_m64|前 4 個參數 – RCX、RDX、R8、R9。  其他的會透過堆疊傳遞。|  
|彙總 \(其他\)|以指標傳遞。  前 4 個參數會在 RCX、RDX、R8 和 R9 中傳遞為指標。|  
|\_\_m128|以指標傳遞。  前 4 個參數會在 RCX、RDX、R8 和 R9 中傳遞為指標。|  
  
## 引數傳遞的範例 1 – 全部是整數  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## 引數傳遞的範例 2 – 全部是浮點數  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## 引數傳遞的範例 3 – 混合整數和浮點數  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## 引數傳遞的範例 4 –\_\_m64、\_\_m128 和彙總  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)