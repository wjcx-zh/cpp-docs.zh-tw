---
title: "編譯器錯誤 C3367 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3367
dev_langs: C++
helpviewer_keywords: C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e341266c37411d96a4cf313e6a101e48aeb2a85d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3367"></a>編譯器錯誤 C3367
'static_member_function' : 無法用靜態函式建立未繫結的委派  
  
當您呼叫未繫結的委派時，您必須傳遞物件的執行個體。 由於是透過類別名稱呼叫靜態成員函式，您只能以執行個體成員函式具現化未繫結的委派。  
  
如需未繫結的委派的詳細資訊，請參閱[如何： 定義和使用委派 (C + + /CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3367：  
  
```cpp  
// C3367.cpp  
// compile with: /clr  
ref struct R {  
   void b() {}  
   static void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::b);   // OK  
   Del ^ b = gcnew Del(&R::f);   // C3367  
}  
```