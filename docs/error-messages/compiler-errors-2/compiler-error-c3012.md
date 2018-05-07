---
title: 編譯器錯誤 C3012 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d30a7fbb50a984c8cec6b45a0ab4759a0578de7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3012"></a>編譯器錯誤 C3012
  
> '*內建*': 不允許直接放在平行區域內的內建函式  
  
 A[編譯器內建](../../intrinsics/compiler-intrinsics.md)中不允許函式`omp parallel`區域。 若要修正此問題，請移動內建函式超出區域，或取代非內建的對等項目。   
  
## <a name="example"></a>範例  
  
 下列範例會產生 C3012，並示範修正此問題的一種方法：  
  
```cpp  
// C3012.cpp  
// compile with: /openmp  
#ifdef __cplusplus  
extern "C" {  
#endif  
void* _ReturnAddress();  
#ifdef __cplusplus  
}  
#endif  
  
int main()  
{  
   #pragma omp parallel  
   {  
      _ReturnAddress();   // C3012  
   }  
   _ReturnAddress();      // OK  
}  
```