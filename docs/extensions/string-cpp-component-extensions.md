---
title: 字串  (C++/CLI 和 C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: b9da900ffbfff34dc596d8981095d8285bf37208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171940"
---
# <a name="string--ccli-and-ccx"></a>字串  (C++/CLI 和 C++/CX)

Windows 執行階段和 Common Language Runtime 會將字串表示為配置的記憶體會自動管理的物件。 也就是說，當字串變數超出範圍或應用程式結束時，您不需要明確捨棄字串的記憶體。 若要指示系統會自動管理字串物件的存留期，請宣告包含[物件控制代碼 (^)](handle-to-object-operator-hat-cpp-component-extensions.md) 修飾詞的字串型別。

## <a name="windows-runtime"></a>Windows 執行階段

Windows 執行階段架構要求 `String` 資料類型位於 `Platform` 命名空間。 為了方便起見，Visual C++ 也在 `string` 命名空間中提供了 `Platform::String` 資料類型，這是 `default` 的同義字。

### <a name="syntax"></a>語法

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

使用 `/clr` 進行編譯，編譯器會將字串常值轉換為 <xref:System.String> 型別的字串。 為保留與現有程式碼的回溯相容性，這種情形有兩個例外狀況：

- 例外狀況處理。 擲回字串常值時，編譯器會將它作為字串常值加以攔截。

- 樣板推算。 字串常值以樣板引數方式傳遞時，編譯器會不將它轉換成 <xref:System.String>。 請注意，以泛型引數方式傳遞的字串常值將會升階為 <xref:System.String>。

編譯器也內建支援三個運算子，您可以將它們覆寫以自訂其行為：

- System::String^ operator +( System::String, System::String);

- System::String^ operator +( System::Object, System::String);

- System::String^ operator +( System::String, System::Object);

傳遞 <xref:System.String> 時，如有必要，編譯器將進行 box 作業，然後串連物件 (使用 ToString) 與字串。

> [!NOTE]
> 插入點 ("^") 表示宣告的變數為 C++/CLI 受控物件的控制代碼。

如需詳細資訊，請參閱[字串和字元常值](../cpp/string-and-character-literals-cpp.md)。

### <a name="requirements"></a>需求

編譯器選項： **/clr**

### <a name="examples"></a>範例

以下程式碼範例會示範串連和比較字串。

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

以下範例會示範您可以多載編譯器提供的運算子，以及編譯器將會發現以 <xref:System.String> 型別為基礎的函式多載。

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

以下範例會示範編譯器如何區別原生字串和 <xref:System.String> 字串。

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)<br/>
[字串和字元常值](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (通用語言執行平台編譯)](../build/reference/clr-common-language-runtime-compilation.md)
