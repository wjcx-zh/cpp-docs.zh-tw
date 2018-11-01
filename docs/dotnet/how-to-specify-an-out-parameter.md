---
title: 如何：指定 out 參數
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 8c3499a2916eda7ab96f7958df190c803206741e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437065"
---
# <a name="how-to-specify-an-out-parameter"></a>如何：指定 out 參數

此範例示範如何指定函式參數是輸出參數以及如何從 C# 程式呼叫該函式。

使用 Visual c + + 中指定 out 參數<xref:System.Runtime.InteropServices.OutAttribute>。

## <a name="example"></a>範例

此範例的第一個部分是 Visual c + + DLL 包含 out 參數的函式的類型。

```
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

這是使用上一個範例中所建立的 Visual c + + 元件的 C# 用戶端。

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

## <a name="see-also"></a>另請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)