---
title: 常值 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
dev_langs:
- C++
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8168b3cd981bb288df35659ffd3520a7c8597d1e
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328062"
---
# <a name="literal-ccli-and-ccx"></a>常值 (C + + /cli 和 C + + /CX)

變數 （資料成員） 將會標示**常值**中 **/clr**編譯為原生相當於**靜態 const**變數。

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

資料成員標記為**常值**必須在宣告時初始化而且此值必須是常數整數、 列舉或字串類型。 從初始化運算式的類型轉換成靜態常數資料成員的類型時，不可要求使用者定義的轉換。

在執行階段不會為常值欄位配置記憶體，編譯器只會在類別的中繼資料內插入其值。

變數標示**靜態 const**將無法使用其他編譯器的中繼資料內。

如需詳細資訊，請參閱 <<c0> [ 靜態](../cpp/storage-classes-cpp.md)並[const](../cpp/const-cpp.md)。

**常值**是內容相關性關鍵字。 請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

這個範例將示範**常值**變數表示**靜態**。

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

## <a name="example"></a>範例

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

## <a name="example"></a>範例

下列範例中，以 C# 中，撰寫參考先前範例中所建立的中繼資料，並顯示的影響**常值**並**靜態 const**變數：

```cs
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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)