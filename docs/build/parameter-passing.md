---
title: "參數傳遞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0359a6cbbb1f646432b03722cdf4ba3010cffa72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="parameter-passing"></a>參數傳遞
前四個整數引數會傳入暫存器。 整數值會在 RCX、 RDX、 R8 和 R9 中傳遞 （在由左到右的順序）。 五個引數和更新版本會在堆疊上傳遞。 所有引數是在暫存器中靠右對齊。 這是讓被呼叫端可以略過暫存器的較高的位元，如果需要可以存取暫存器所需的部分。  
  
 浮點數和雙精確度的引數會傳入 XMM0: XMM3 （最多 4) 與整數插槽 （RCX、 RDX、 R8 和 R9），通常會使用該基數位置所忽略 （請參閱範例），反之亦然。  
  
 [__m128](../cpp/m128.md)類型、 陣列和字串會永遠不會傳遞以即時運算值但而是將指標傳遞至呼叫端所配置的記憶體。 傳遞結構/等位的大小為 8、 16、 32 或 64 位元和 __m64 如同它們是相同大小的整數。 這些大小以外的結構/等位的指標傳遞至呼叫端所配置的記憶體。 當做指標傳遞給這些彙總類型 (包括\__m128)，呼叫端配置的暫存記憶體將會是 16 個位元組對齊。  
  
 未配置堆疊空間，以及不呼叫其他函式的內建函式可以使用其他動態暫存器，來將其他暫存器引數傳遞，因為編譯器和內建函式實作之間的緊密繫結。 這是進一步改善效能的機會。  
  
 被呼叫端有責任傾印到其陰影空間，如有需要的暫存器參數。  
  
 下表摘要說明如何傳遞參數：  
  
|參數型別|如何傳遞|  
|--------------------|----------------|  
|浮點|第一次參數 4-透過 XMM3 XMM0。 其他人堆疊上傳遞。|  
|整數|第一次參數 4-RCX、 RDX、 R8 R9。 其他人堆疊上傳遞。|  
|彙總 （8、 16、 32、 或 64 位元） 和 __m64|第一次參數 4-RCX、 RDX、 R8 R9。 其他人堆疊上傳遞。|  
|彙總 （其他）|由指標。 當做指標 RCX、 RDX、 R8 和 R9 中傳遞的前 4 個參數|  
|__m128|由指標。 當做指標 RCX、 RDX、 R8 和 R9 中傳遞的前 4 個參數|  
  
## <a name="example-of-argument-passing-1---all-integers"></a>傳遞 1-所有整數引數的範例  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-2---all-floats"></a>引數傳遞 2-所有浮點數的範例  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>引數傳遞 3-混合的整數和浮點數的範例  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>引數傳遞 4 的範例-__m64、 \__m128，和彙總  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../build/calling-convention.md)