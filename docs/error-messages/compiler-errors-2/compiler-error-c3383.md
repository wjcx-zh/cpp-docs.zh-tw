---
title: "編譯器錯誤 C3383 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2a97cd1348bc927b633e683bed80a6b907f88a58
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3383"></a>編譯器錯誤 C3383
/clr:safe 不支援 'operator new'  
  
 **/clr:safe** 編譯的輸出檔是可驗證類型安全的檔案，並且不支援指標。  
  
 如需詳細資訊，請參閱：  
  
-   [/clr （common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Visual C++ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>範例  
 下列範例會產生 C3383。  
  
```  
// C3383.cpp  
// compile with: /clr:safe  
int main() {  
   char* pCharArray = new char[256];  // C3383  
}  
```
