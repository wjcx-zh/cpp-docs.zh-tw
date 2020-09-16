---
title: literal (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: 2687352c02bed609ffaa60ee8b1df40b51126d21
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686726"
---
# <a name="literal-ccli-and-ccx"></a>literal (C++/CLI 和 C++/CX)

在 **/clr** 編譯中標記為 **literal** 的變數 (資料成員) 是 **static const** 變數的原生對等用法。

## <a name="all-platforms"></a>所有平台

### <a name="remarks"></a>備註

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

(這個語言功能沒有只適用於 Windows 執行階段的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>備註

標記為 **literal** 的資料成員必須在宣告時初始化，而且值必須是常數整數、列舉或字串類型。 從初始化運算式的類型轉換成靜態常數資料成員的類型時，不可要求使用者定義的轉換。

在執行階段不會為常值欄位配置記憶體，編譯器只會在類別的中繼資料內插入其值。

標記為 **static const** 的變數將不會在中繼資料內提供給其他編譯器。

如需詳細資訊，請參閱 [Static](../cpp/storage-classes-cpp.md) 與 [const](../cpp/const-cpp.md)。

**literal** 是即時線上關鍵字。 如需詳細資訊，請參閱[即時線上關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="examples"></a>範例

此範例顯示 **常** 值變數表示 **`static`** 。

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

下列範例將示範中繼資料內常值的影響：

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

請注意 `sc` 和 `lit` 之中繼資料內的差異：`modopt` 指示詞會套用至 `sc`，這表示其他編譯器可以忽略它。

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

下列範例是以 C# 撰寫，會參考先前範例中建立的中繼資料，並顯示 **literal** 和 **static const** 變數的影響：

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[適用于 .NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
