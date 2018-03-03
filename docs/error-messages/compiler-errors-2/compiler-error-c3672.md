---
title: "編譯器錯誤 C3672 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3672
dev_langs:
- C++
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b47d6a6f565ccd569c68a500974a0e185b1da21a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3672"></a>編譯器錯誤 C3672
虛擬解構函式運算式只能做為函式呼叫的一部分  
  
 未正確地呼叫解構函式。  如需詳細資訊，請參閱[解構函式](../../cpp/destructors-cpp.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3672。  
  
```  
// C3672.cpp  
template<typename T>  
void f(T* pT) {  
   &pT->T::~T;   // C3672  
   pT->T::~T();   // OK  
};  
  
int main() {  
   int i;  
   f(&i);  
}  
```