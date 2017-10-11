---
title: "編譯器錯誤 C3382 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3382
dev_langs:
- C++
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 782e5c4cc61294dbdaecbd63ff5c6031d387f843
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3382"></a>編譯器錯誤 C3382
/clr:safe 不支援 'sizeof'  
  
 **/clr:safe** 編譯的輸出檔是可驗證類型安全的檔案，而且不支援 sizeof，因為 sizeof 運算子的傳回值是 size_t，其大小視作業系統而異。  
  
 如需詳細資訊，請參閱：  
  
-   [sizeof 運算子](../../cpp/sizeof-operator.md)  
  
-   [/clr （common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C++ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>範例  
 下列範例會產生 C3382。  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```
