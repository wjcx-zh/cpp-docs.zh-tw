---
title: 字串 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/08/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fd4caaf49bd72a85a6d81003926c4e556d0731e0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054237"
---
# <a name="string--ccli-and-ccx"></a>字串 (C + + /cli 和 C + + /CX)

Windows 執行階段和通用語言執行平台代表字串做為其配置的記憶體自動管理的物件。 也就是說，您不需要明確的字串變數超出範圍或您的應用程式結束時，捨棄字串的記憶體。 若要表示的字串物件的存留期自動管理，宣告 string 型別與[控制代碼物件 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)修飾詞。

## <a name="windows-runtime"></a>Windows 執行階段

Windows 執行階段架構要求`String`資料型別位於`Platform`命名空間。 為了方便起見，Visual c + + 也提供`string`資料類型，這是的同義字`Platform::String`，請在`default`命名空間。

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

進行編譯時`/clr`，編譯器會將字串常值轉換為字串型別的<xref:System.String>。 若要保留與現有程式碼的回溯相容性是兩個例外狀況：

- 例外狀況處理。 擲回字串常值時，編譯器會攔截它的字串常值。

- 樣板推斷。 字串常值傳遞做為範本引數時，編譯器會不將它轉換成<xref:System.String>。 請注意，傳遞做為泛型引數的字串常值將會升級為<xref:System.String>。

編譯器也會有三個運算子，您可以覆寫以自訂其行為的內建支援：

- System:: string ^ 運算子 + system:: string (system:: string）;

- System:: string ^ 運算子 + (system:: object，system:: string);

- System:: string ^ 運算子 + (system:: string，system:: object);

當傳遞<xref:System.String>，編譯器將方塊中，如有必要，然後再進行串連的字串 （使用 ToString) 物件。

> [!NOTE]
> 插入號 ("^") 表示宣告的變數是控制代碼的 C + + /cli CLI managed 物件。

如需詳細資訊，請參閱[String and Character Literals](../cpp/string-and-character-literals-cpp.md)。

### <a name="requirements"></a>需求

編譯器選項： **/clr**

### <a name="examples"></a>範例

下列程式碼範例示範如何串連和比較字串。

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

下列範例會示範您可以多載的編譯器提供的運算子，與編譯器，會看到根據函式多載<xref:System.String>型別。

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

下列範例會示範編譯器會區別原生字串和<xref:System.String>字串。

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)<br/>
[字串和字元常值](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (通用語言執行平台編譯)](../build/reference/clr-common-language-runtime-compilation.md)