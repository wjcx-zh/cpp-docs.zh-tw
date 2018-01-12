---
title: "編譯器警告 （層級 4） C4263 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4263
dev_langs: C++
helpviewer_keywords: C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47f871f956ef07eebc2f528182dde58ba0fa3b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4263"></a>編譯器警告 (層級 4) C4263
'function': 成員函式不會覆寫任何基底類別虛擬成員函式  
  
 函式類別定義具有相同名稱的基底類別，但不是相同類型或數目的引數中的虛擬函式。 這可以有效地隱藏基底類別中的虛擬函式。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 下列範例會產生 C4263:  
  
```  
// C4263.cpp  
// compile with: /W4  
#pragma warning(default:4263)  
#pragma warning(default:4264)  
class B {  
public:  
   virtual void func();  
};  
  
class D : public B {  
   void func(int);   // C4263  
};  
  
int main() {  
}  
```