---
title: 編譯器錯誤 C3421 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3421
dev_langs:
- C++
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 441bfb9d9c5f48b7531b92581a9bf6aad31b38ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255288"
---
# <a name="compiler-error-c3421"></a>編譯器錯誤 C3421
'type' : 您不能呼叫這個類別的完成項，因為它無法存取，或者不存在  
  
 完成項是隱含私用的，因此無法從其封入類型外部呼叫。  
  
 如需詳細資訊，請參閱[解構函式與完成項中如何： 定義和使用類別和結構 (C + + /CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3421。  
  
```  
// C3421.cpp  
// compile with: /clr  
ref class A {};  
  
ref class B {   
   !B() {}  
  
public:  
   ~B() {}  
};  
  
int main() {  
   A a;  
   a.!A();   // C3421  
  
   B b;  
   b.!B();   // C3421  
}  
```