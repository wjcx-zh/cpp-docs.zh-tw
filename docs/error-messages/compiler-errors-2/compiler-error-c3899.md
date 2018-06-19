---
title: 編譯器錯誤 C3899 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3899
dev_langs:
- C++
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f40f1065514437463be06a89f01e067c4324cd2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275992"
---
# <a name="compiler-error-c3899"></a>編譯器錯誤 C3899
'var': initonly 資料成員的左值使用不允許直接放在類別 'class' 中的平行區域內  
  
 [Initonly (C + + /CLI)](../../dotnet/initonly-cpp-cli.md)無法初始化資料成員，該部分所用的建構函式內[平行](../../parallel/openmp/reference/parallel.md)區域。  這是因為編譯器會內部的重新配置，該程式碼，使它不再有效的建構函式的一部分。  
  
 若要解決，初始化建構函式，但在平行區域外的 initonly 資料成員。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3899。  
  
```  
// C3899.cpp  
// compile with: /clr /openmp  
#include <omp.h>   
  
public ref struct R {  
   initonly int x;  
   R() {  
      x = omp_get_thread_num() + 1000;   // OK  
      #pragma omp parallel num_threads(5)  
      {  
         // cannot assign to 'x' here  
         x = omp_get_thread_num() + 1000;   // C3899  
         System::Console::WriteLine("thread {0}", omp_get_thread_num());  
      }  
      x = omp_get_thread_num() + 1000;   // OK  
   }  
};  
  
int main() {  
   R^ r = gcnew R;  
   System::Console::WriteLine(r->x);  
}  
```