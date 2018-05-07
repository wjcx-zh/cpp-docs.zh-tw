---
title: 編譯器錯誤 C3390 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3390
dev_langs:
- C++
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc731f714976d8ab32c5e7a629d008fde008a218
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3390"></a>編譯器錯誤 C3390
'type_arg' : 對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，必須是參考類型  
  
泛型類型未正確地具現化。  請檢查類型定義。  如需詳細資訊，請參閱[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
第一個範例會使用 C#，建立包含具有 C + 中撰寫泛型類型時，不支援的特定條件約束的泛型類型的元件 + CLR。 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。  
  
```cs  
// C3390.cs  
// Compile by using: csc /target:library C3390.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
可用 C3390.dll 元件時，下列範例會產生 C3390。  
  
```cpp  
// C3390_b.cpp  
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>  
ref class R { R(int) {} };  
value class V {};  
ref struct N { N() {} };  
  
int main () {  
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type  
   GR<R^, V, N^>^ gr2b; // OK  
}  
```