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
ms.openlocfilehash: b91918d526d83d4cf47436d02b7c67038576bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152762"
---
# <a name="managed-types-ccli"></a>Managed 類型 (C++/CLI)

視覺化C++可讓您透過 managed 型別，其提供通用語言執行平台功能的支援，但有可能的優點和限制的執行階段的.NET 功能存取。

## <a name="main_functions"></a> Managed 的類型和 main 函式

撰寫應用程式使用時 **/clr**的引數**main （)** 函式不能是 managed 型別。

是適當的簽章的範例：

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="dotnet"></a> .NET framework 對應項C++原生類型

下表顯示內建的視覺效果的關鍵字C++類型，也就是預先定義的型別的別名中**系統**命名空間。

|視覺化C++型別|.NET Framework 類型|
|-----------------------|-------------------------|
|**void**|<xref:System.Void?displayProperty=nameWithType>|
|**bool**|<xref:System.Boolean?displayProperty=nameWithType>|
|**帶正負號的 char** |<xref:System.SByte?displayProperty=nameWithType>|
|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|
|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|
|**簡短**和**帶正負號短**|<xref:System.Int16?displayProperty=nameWithType>|
|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|
|**int**，**帶正負號 int**， **long**，和**帶正負號長時間**|<xref:System.Int32?displayProperty=nameWithType>|
|**不帶正負號的 int**和**不帶正負號長時間**|<xref:System.UInt32?displayProperty=nameWithType>|
|**__int64**和**帶正負號的 __int64**|<xref:System.Int64?displayProperty=nameWithType>|
|**unsigned __int64**|<xref:System.UInt64?displayProperty=nameWithType>|
|**float**|<xref:System.Single?displayProperty=nameWithType>|
|**雙精度浮點**和**長雙精度**|<xref:System.Double?displayProperty=nameWithType>|

如需有關預設為帶正負號或不帶正負號的編譯器選項**char**，請參閱[/J （預設 char 類型為不帶正負號）](../build/reference/j-default-char-type-is-unsigned.md)。

## <a name="version_issues"></a> 在原生類型中巢狀的實值型別的版本問題

請考慮用來建置用戶端組件的帶正負號 （強式名稱） 組件元件。 元件包含在用戶端當做類型使用的原生的等位、 類別或陣列成員的實值型別。 如果未來版本的元件變更的大小或值類型的配置，就必須重新編譯用戶端。

建立與 keyfile [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`)。

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

### <a name="output"></a>Output

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>註解

不過，如果您新增另一個成員，才能`struct S`nested_value_types.cpp，在 (例如`double d;`) 並重新編譯元件，不需要重新編譯用戶端，結果就是未處理的例外狀況 (型別的<xref:System.IO.FileLoadException?displayProperty=fullName>)。

## <a name="test_equality"></a>如何：測試相等

在下列範例中，測試是否相等，會使用 Managed Extensions forC++為基礎的控制代碼的參考。

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

此程式 IL 顯示使用 op_Equality 呼叫實作傳回的值。

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="diagnose_fix"></a>如何：診斷和修正組件相容性問題

本主題說明在編譯時期參考的組件的版本不符合在執行階段，參考的組件的版本時，會發生什麼情況，以及如何避免發生問題。

當編譯組件時，可能會使用參考其他組件`#using`語法。 在編譯期間，這些組件是由編譯器所存取。 這些組件中的資訊用來進行最佳化的決策。

不過，如果變更或重新編譯參考的組件時，您不重新編譯參考的組件相依於它的組件可能不相容。 在有效的最佳化決策第一次可能不是正確的新組件版本。 多個執行階段錯誤可能是因為這些不相容情況。 沒有特定的例外狀況會在此情況下產生。 在執行階段回報的失敗的方式取決於程式碼變更造成問題的本質。

這些錯誤不應最終的實際執行程式碼中的問題，只要您的產品發行版本都會建立整個應用程式。 公開發行的組件應該標示官方的版本號碼，如此可確保可避免這些問題。 如需詳細資訊，請參閱[組件版本控制](/dotnet/framework/app-domains/assembly-versioning)。

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>診斷和修復不相容錯誤

1. 如果您遇到執行階段例外狀況或其他參考另一個組件，程式碼中發生的錯誤狀況，而且找不到問題起因，您可能會處理過期的組件。

1. 首先，找出並重現或其他錯誤狀況的例外狀況。 因為發生過期的例外狀況，就會發生的問題應該是可重現。

1. 請檢查您的應用程式中參考的任何組件的時間戳記。

1. 如果任何參考組件的時間戳記晚於您的應用程式的最後一個編譯的時間戳記，您的應用程式已過期。 如果發生這種情況，重新編譯您的應用程式的最新的組件，並進行任何所需的程式碼變更。

1. 重新執行應用程式，請執行重現問題，並確認不會不會發生例外狀況的步驟。

### <a name="example"></a>範例

下列程式說明的問題，透過減少; 方法的協助工具，並嘗試存取另一個組件中的該方法不需要重新編譯。 嘗試編譯`changeaccess.cpp`第一次。 這是所參考的組件會變更。 然後，編譯`referencing.cpp`。 編譯會成功。 現在，以減少呼叫的方法的存取範圍。 重新編譯`changeaccess.cpp`旗標`/DCHANGE_ACCESS`。 這會讓方法受到保護，而非私用，因此您可以再呼叫合法。 不需要重新編譯`referencing.exe`，重新執行應用程式。 例外狀況<xref:System.MethodAccessException>會產生。

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

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[與其他 .NET 語言間的互通性 (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Managed 類型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)
