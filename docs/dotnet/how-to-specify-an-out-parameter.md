---
title: HOW TO：指定 out 參數
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 901257b92aaa5e13e6e79d612ca590b734e15881
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387212"
---
# <a name="how-to-specify-an-out-parameter"></a>HOW TO：指定 out 參數

此範例示範如何指定函式參數是輸出參數以及如何從 C# 程式呼叫該函式。

Out 參數指定在視覺效果C++具有<xref:System.Runtime.InteropServices.OutAttribute>。

## <a name="example"></a>範例

此範例的第一個部分是視覺效果C++DLL 包含 out 參數的函式的類型。

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

這是C#用戶端使用視覺效果C++在上述範例中所建立的元件。

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
