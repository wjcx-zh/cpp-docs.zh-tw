---
title: 如何：指定 out 參數
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 5f0b462e672de4408d50bf95d65c749bf1881078
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988433"
---
# <a name="how-to-specify-an-out-parameter"></a>如何：指定 out 參數

這個範例會示範如何指定函式參數為 out 參數，以及如何從C#程式呼叫該函數。

在具有 <xref:System.Runtime.InteropServices.OutAttribute> 的視覺效果C++中指定 out 參數。

## <a name="example"></a>範例

這個範例的第一個部分是一個 Visual C++ DLL，其型別包含含有 out 參數的函式。

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>範例

這是使用C#上一個範例中所C++建立之視覺元件的用戶端。

```
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
