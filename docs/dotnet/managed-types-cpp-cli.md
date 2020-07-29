---
title: Managed 類型 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: c542151bda780e5306db35049d988e6514fffd62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225601"
---
# <a name="managed-types-ccli"></a>Managed 類型 (C++/CLI)

Visual C++ 允許透過 managed 類型存取 .NET 功能，以提供 common language runtime 功能的支援，並受限於執行時間的優點和限制。

## <a name="managed-types-and-the-main-function"></a><a name="main_functions"></a>Managed 類型和 main 函式

使用撰寫應用程式時 **`/clr`** ， **main （）** 函數的引數不能是 managed 類型。

適當簽章的範例如下：

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="net-framework-equivalents-to-c-native-types"></a><a name="dotnet"></a>C + + 原生類型的 .NET Framework 對等專案

下表顯示內建 Visual C++ 類型的關鍵字，這些是**System**命名空間中預先定義類型的別名。

|Visual C++ 類型|.NET Framework 類型|
|-----------------------|-------------------------|
|**`void`**|<xref:System.Void?displayProperty=nameWithType>|
|**`bool`**|<xref:System.Boolean?displayProperty=nameWithType>|
|**`signed char`** |<xref:System.SByte?displayProperty=nameWithType>|
|**`unsigned char`**|<xref:System.Byte?displayProperty=nameWithType>|
|**`wchar_t`**|<xref:System.Char?displayProperty=nameWithType>|
|**`short`** 和**`signed short`**|<xref:System.Int16?displayProperty=nameWithType>|
|**`unsigned short`**|<xref:System.UInt16?displayProperty=nameWithType>|
|**`int`**、 **`signed int`** 、 **`long`** 和**`signed long`**|<xref:System.Int32?displayProperty=nameWithType>|
|**`unsigned int`** 和**`unsigned long`**|<xref:System.UInt32?displayProperty=nameWithType>|
|**`__int64`** 和**`signed __int64`**|<xref:System.Int64?displayProperty=nameWithType>|
|**`unsigned __int64`**|<xref:System.UInt64?displayProperty=nameWithType>|
|**`float`**|<xref:System.Single?displayProperty=nameWithType>|
|**`double`** 和**`long double`**|<xref:System.Double?displayProperty=nameWithType>|

如需編譯器選項預設為或的詳細資訊 **`signed char`** **`unsigned char`** ，請參閱[ `/J` （預設 **`char`** 類型為 **`unsigned`** ）](../build/reference/j-default-char-type-is-unsigned.md)。

## <a name="version-issues-for-value-types-nested-in-native-types"></a><a name="version_issues"></a>在原生類型中嵌套實數值型別的版本問題

請考慮用來建立用戶端元件的帶正負號（強式名稱）元件元件。 元件包含實值型別，可在用戶端中用來做為原生等位、類別或陣列成員的型別。 如果元件的未來版本變更了實數值型別的大小或配置，則必須重新編譯用戶端。

使用[sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) （）建立 keyfile `sn -k mykey.snk` 。

### <a name="example"></a>範例

下列範例是元件。

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>範例

這個範例是用戶端：

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>輸出

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>評價

不過，如果您在 nested_value_types .cpp 中將另一個成員加入至 `struct S` （例如 `double d;` ），並在不重新編譯用戶端的情況下重新編譯元件，則結果會是未處理的例外狀況（類型為 <xref:System.IO.FileLoadException?displayProperty=fullName> ）。

## <a name="how-to-test-for-equality"></a><a name="test_equality"></a>如何：測試是否相等

在下列範例中，使用 Managed Extensions for C++ 的相等測試是根據控制碼所參考的內容。

### <a name="example"></a>範例

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

此程式的 IL 顯示，傳回值是使用 op_Equality 的呼叫來執行。

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="how-to-diagnose-and-fix-assembly-compatibility-problems"></a><a name="diagnose_fix"></a>如何：診斷和修正元件相容性問題

本主題說明在編譯時期參考的元件版本與執行時間所參考的元件版本不相符時，會發生什麼情況，以及如何避免這個問題。

編譯元件時，可能會使用語法來參考其他元件 `#using` 。 在編譯期間，編譯器會存取這些元件。 這些元件中的資訊是用來做出優化決策。

不過，如果參考的元件已變更並重新編譯，而且您不重新編譯相依于它的參考元件，則元件可能仍然不相容。 相對於新元件版本而言，第一次有效的優化決策可能不正確。 可能會因為這些不相容而發生各種執行階段錯誤。 在這種情況下，並不會產生特定的例外狀況。 在執行時間報告失敗的方式，取決於造成問題之程式碼變更的本質。

只要針對產品的發行版本重建整個應用程式，這些錯誤就應該不會在最終的實際執行程式碼中發生問題。 發行至公用的元件應該以官方版本號碼標示，這可確保避免這些問題。 如需詳細資訊，請參閱[組件版本控制](/dotnet/framework/app-domains/assembly-versioning)。

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>診斷和修正不相容錯誤

1. 如果您遇到執行時間例外狀況，或是在程式碼中發生的其他錯誤情況會參考另一個元件，而且沒有其他識別的原因，您可能會處理過期的元件。

1. 首先，隔離並重現例外狀況或其他錯誤情況。 因過期的例外狀況而發生的問題應該可以重現。

1. 檢查應用程式中所參考之任何元件的時間戳記。

1. 如果任何參考元件的時間戳記晚于應用程式上次編譯的時間戳記，則您的應用程式已過期。 如果發生這種情況，請使用最新的元件重新編譯您的應用程式，並進行任何必要的程式碼變更。

1. 重新執行應用程式，並執行重現問題的步驟，並確認不會發生例外狀況。

### <a name="example"></a>範例

下列程式會藉由減少方法的存取範圍並嘗試在另一個元件中存取該方法，來說明問題，而不需要重新編譯。 請先嘗試編譯 `changeaccess.cpp` 。 這是所參考的元件，將會變更。 然後編譯 `referencing.cpp` 。 編譯成功。 現在，減少所呼叫方法的存取範圍。 使用旗標重新編譯 `changeaccess.cpp` `/DCHANGE_ACCESS` 。 這會讓方法受到保護，而不是私用，因此可以更長的合法方式呼叫。 若未 `referencing.exe` 重新編譯，請重新執行應用程式。 <xref:System.MethodAccessException>將會產生例外狀況。

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>另請參閱

[使用 c + +/CLI 進行 .NET 程式設計（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[與其他 .NET 語言的互通性（c + +/CLI）](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Managed 類型（c + +/CLI）](../dotnet/managed-types-cpp-cli.md)<br/>
[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)
