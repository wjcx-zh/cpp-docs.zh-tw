---
title: 編譯器錯誤 C3005 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3005
dev_langs:
- C++
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80c0bdb0f17670c5acd178b7eadcbc6d3868637c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245187"
---
# <a name="compiler-error-c3005"></a>編譯器錯誤 C3005
'error_text'：OpenMP 'directive' 指示詞上有未預期的語彙基元  
  
 OpenMP 指示詞的格式錯誤。  
  
 下列範例會產生 C3005：  
  
```  
// C3005.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp parallel + for   // C3005  
}  
```  
  
 如果左大括弧和 pragma 放在同一行中，也會發生 C3005。  
  
```  
// C3005b.c  
// compile with: /openmp  
int main() {  
   #pragma omp parallel {   // C3005 put open brace on next line  
   lbl2:;  
   }  
   goto lbl2;  
}  
```