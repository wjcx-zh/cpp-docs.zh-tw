---
title: "編譯器錯誤 C2720 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfd1e41ea3b9479f07faa9a1cbf0739bc0b7e8b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2720"></a>編譯器錯誤 C2720  
  
> '*識別碼*':'*規範*' 儲存類別規範不合法成員上  
  
儲存類別不能在宣告之外的類別成員上使用。 若要修正這個錯誤，移除不需要[儲存類別](../../cpp/storage-classes-cpp.md)規範定義中的類別宣告之外的成員。  
  
## <a name="example"></a>範例  
  
下列範例會產生 C2720，並示範如何修正此問題：  
  
```cpp  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
```