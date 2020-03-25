---
title: Boxing  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- boxing, C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
ms.openlocfilehash: 709754e8609406f635444937af93488060167ba9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172603"
---
# <a name="boxing--ccli-and-ccx"></a>Boxing  (C++/CLI 和 C++/CX)

將實值型別轉換為物件的作業稱為 *boxing*，而將物件轉換為實值型別的作業稱為 *unboxing*。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

C++/CX 支援用於 boxing 實值類型和 unboxing 參考類型的速記語法。 指派給類型 `Object` 的變數時，會對實值類型進行 boxed 處理。 將 `Object` 變數指派給實值類型變數時會進行 unboxed 處理，並且在括號中指定 unboxed 類型；也就是說，物件變數會轉換成實值類型。

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

下列程式碼示範對 `DateTime` 值進行 box 和 unbox 處理。 首先，範例會取得表示目前日期和時間的 `DateTime` 值，並將它指派給 `DateTime` 變數。 然後透過將 `DateTime` 指派給 `Object` 變數進行 boxing 處理。 最後，透過將已進行 boxing 處理的值指派給另一個 `DateTime` 變數來進行 unboxing 處理。

若要測試此範例，請建立一個 `BlankApplication` 專案、取代 `BlankPage::OnNavigatedTo()` 方法，然後在右括號位置指定中斷點，並指定指派給變數 `str1`。 當範例到達右括號位置時，檢查 `str1`。

```cpp
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    using namespace Windows::Globalization::DateTimeFormatting;

    Windows::Foundation::DateTime dt, dtAnother;
    Platform::Object^ obj1;

    Windows::Globalization::Calendar^ c =
        ref new Windows::Globalization::Calendar;
    c->SetToNow();
    dt = c->GetDateTime();
    auto dtf = ref new DateTimeFormatter(
                           YearFormat::Full,
                           MonthFormat::Numeric,
                           DayFormat::Default,
                           DayOfWeekFormat::None);
    String^ str1 = dtf->Format(dt);
    OutputDebugString(str1->Data());
    OutputDebugString(L"\r\n");

    // Box the value type and assign to a reference type.
    obj1 = dt;
    // Unbox the reference type and assign to a value type.
    dtAnother = (Windows::Foundation::DateTime) obj1;

    // Format the DateTime for display.
    String^ str2 = dtf->Format(dtAnother);
    OutputDebugString(str2->Data());
}
```

如需詳細資訊，請參閱 [Boxing (C++/CX)](../cppcx/boxing-c-cx.md)。

## <a name="common-language-runtime"></a>Common Language Runtime

編譯器會將實值型別進行 boxing 處理為 <xref:System.Object>。 這是可行的，因為編譯器所定義的轉換可將實值類型轉換為 <xref:System.Object>。

boxing 和 unboxing 可讓實值類型被視為物件。 實值類型，包括結構類型和內建類型 (如 int)，可以往返轉換為類型 <xref:System.Object>。

如需詳細資訊，請參閱

- [如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)

- [如何：使用 gcnew 建立實值型別及使用隱含 Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [如何：Unbox](../dotnet/how-to-unbox.md)

- [標準轉換和隱含 Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例示範隱含 Boxing 如何運作。

```cpp
// vcmcppv2_explicit_boxing2.cpp
// compile with: /clr
using namespace System;

ref class A {
public:
   void func(System::Object^ o){Console::WriteLine("in A");}
};

value class V {};

interface struct IFace {
   void func();
};

value class V1 : public IFace {
public:
   virtual void func() {
      Console::WriteLine("Interface function");
   }
};

value struct V2 {
   // conversion operator to System::Object
   static operator System::Object^(V2 v2) {
      Console::WriteLine("operator System::Object^");
      return (V2^)v2;
   }
};

void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}
void func1(V2^){Console::WriteLine("in func1(V2^)");}

void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}

int main() {
   // example 1 simple implicit boxing
   Int32^ bi = 1;
   Console::WriteLine(bi);

   // example 2 calling a member with implicit boxing
   Int32 n = 10;
   Console::WriteLine("xx = {0}", n.ToString());

   // example 3 implicit boxing for function calls
   A^ a = gcnew A;
   a->func(n);

   // example 4 implicit boxing for WriteLine function call
   V v;
   Console::WriteLine("Class {0} passed using implicit boxing", v);
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing

   // example 5 casting to a base with implicit boxing
   V1 v1;
   IFace ^ iface = v1;
   iface->func();

   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching
   V2 v2;
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing
                // Will call void func1(System::Object^);

   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)
}
```

```Output
1

xx = 10

in A

Class V passed using implicit boxing

Class V passed with forced boxing

Interface function

in func1(V2^)

in func2(System::ValueType^)

in func2(System::ValueType^)
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
