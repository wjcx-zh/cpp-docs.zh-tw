---
title: 編譯器警告 （層級 1） C4383 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4383
dev_langs:
- C++
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b78209cf4e3e320cca8b161a4e6c99eaca6d771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4383"></a>編譯器警告 (層級 1) C4383
'instance_dereference_operator': 控制代碼取值的意義可以變更，當使用者定義的 'operator' 運算子存在時，將這個運算子撰寫運算元的明確宣告靜態函式  
  
 當您在 managed 類型中新增使用者定義的執行個體的覆寫取值運算子時，您可能會覆寫類型的取值運算子傳回的控制代碼物件的能力。 請考慮撰寫靜態的使用者定義運算子取值 （dereference)。  
  
 如需詳細資訊，請參閱[物件控制代碼運算子 (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md)和[追蹤參考運算子](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
 此外，執行個體運算子不適用於其他語言編譯器，透過參考的中繼資料。 如需詳細資訊，請參閱[使用者定義的運算子 (C + + /CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4383。  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```