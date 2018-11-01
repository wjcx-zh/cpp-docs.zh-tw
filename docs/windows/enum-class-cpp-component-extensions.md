---
title: 列舉類別 (C + + /cli 和 C + + /CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: 5bc850831e961a500ae71ce90e3ca39b3aabd159
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592513"
---
# <a name="enum-class--ccli-and-ccx"></a>列舉類別 (C + + /cli 和 C + + /CX)

在命名空間範圍內宣告列舉，這是使用者定義的類型，由一組稱為列舉值的具名常數所組成。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

C + + /CX 和 C + + 支援**公用列舉類別**並**私用列舉類別**類似於標準 c + +**列舉類別**但加上可存取性規範。 底下 **/clr**，C + + 11**列舉類別**允許型別，但會產生警告 C4472，其要確保您真正想要 ISO 列舉類型，而不是 C + + /CX 和 C + + /cli 的 CLI 型別。 如需有關 ISO 標準 c + + **enum**關鍵字，請參閱[列舉](../cpp/enumerations-cpp.md)。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="syntax"></a>語法

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>參數

*access*<br/>
列舉型別，可協助工具**公開金鑰**或是**私人**。

*列舉識別項*<br/>
列舉名稱。

*基礎類型*<br/>
(選用) 列舉的基礎類型。

(選用。 Windows 執行階段只） 之基礎類型的列舉型別，它可以是**bool**， **char**， `char16`， `int16`， `uint16`， **int**， `uint32`， `int64`，或`uint64`。

*列舉程式清單*<br/>
列舉程式名稱的逗號分隔清單。

每個列舉程式都是常數運算式，不是透過編譯器隱含定義，就是藉由標記法 *列舉程式*`=`*常數運算式*。 如以隱含方式定義，第一個列舉程式的值預設為零。 後續每個以隱含方式定義的列舉程式值，都是前一個列舉程式的值 + 1。

*var*<br/>
(選用) 列舉類型的變數名稱。

### <a name="remarks"></a>備註

如需詳細資訊與範例，請參閱 [列舉](https://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx)。

請注意，如果定義列舉程式值的常數運算式無法以 *基礎類型*表示，編譯器將會發出錯誤訊息。  不過，編譯器不會報告不適合基礎類型之值的錯誤。 例如: 

- 如果 *基礎類型* 是數值，而列舉程式指定了該類型的最大值，則無法表示下一個隱含定義之列舉的值。

- 如果*基礎類型*是**bool**，和兩個以上的列舉值會以隱含方式定義之後無法表示前兩個, 列舉值。

- 如果 *基礎類型* 是 `char16`，而列舉值的範圍是從 0xD800 到 0xDFFF，則可以表示這個值。 不過，此值在邏輯上不正確，因為它代表 Unicode surrogate 字組的一半，不應該單獨出現。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>語法

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>參數

*access*<br/>
列舉的存取範圍。 可以是**公開金鑰**或是**私人**。

*列舉程式清單*<br/>
列舉的識別項 (列舉程式) 逗號分隔清單。

*name*<br/>
列舉名稱。 不允許匿名的 Managed 列舉。

*type*<br/>
（選擇性）基礎類型*識別碼*。 這可以是任何純量類型，例如帶正負號或不帶正負號的版本**int**，**簡短**，或**長**。  **bool**或是**char**也允許。

*var*<br/>
(選用) 列舉類型的變數名稱。

### <a name="remarks"></a>備註

**列舉類別** 和 **列舉結構** 是相同的宣告。

有兩種列舉類型：Managed 或 C++/CX 和標準。

Managed 或 C++/CX 列舉可能定義如下：

```cpp
public enum class day {sun, mon };
```

在語意上相當於：

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

標準列舉可能定義如下：

```cpp
enum day2 { sun, mon };
```

在語意上相當於：

```cpp
static const int sun = 0;
static const int mon = 1;
```

Managed 列舉程式名稱 (*識別項*) 不會插入已定義列舉的範圍，列舉程式的所有參考都必須是完整的 (*名稱*`::`*識別項*)。  為此，您無法定義匿名的 Managed 列舉。

標準列舉的列舉程式會以強式方式插入封閉範圍。  也就是說，如果封閉範圍中另有一個符號與列舉程式同名，編譯器就會產生錯誤。

在 Visual Studio 2002 和 Visual Studio 2003 中，列舉值是弱式方式插入 （會顯示在封閉範圍中除非有另一個具有相同名稱的識別項）。

如果定義了標準 c + + 列舉 (不含**類別**或**結構**)、 編譯與`/clr`會導致將列舉編譯為 managed 列舉。  列舉仍擁有 Unmanaged 列舉的語意。  請注意，編譯器會插入屬性 (attribute)`Microsoft::VisualC::NativeEnumAttribute`以識別程式設計人員的目的是原生列舉的列舉。  其他編譯器只看得到為 Managed 列舉的標準列舉。

使用名為 A，標準列舉編譯`/clr`會顯示為 managed 列舉，組件中，而且可供任何其他 managed 編譯器。   不過，不具名的標準列舉就不會在組件中公開顯示。

在 Visual Studio 2002 和 Visual Studio 2003，標準列舉做為函式參數中的型別：

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

會以 MSIL 格式發出下列項目當做函式簽章：

```cpp
void f(int32);
```

不過，在目前的編譯器版本中，標準列舉是當做附有 [NativeEnumAttribute] 的 Managed 列舉發出，且以 MSIL 格式發出下列項目當做函式簽章：

```cpp
void f(E)
```

如需有關原生列舉的詳細資訊，請參閱 [C++ 列舉宣告](../cpp/enumerations-cpp.md)。

如需有關 CLR 列舉的詳細資訊，請參閱：

- [列舉的基礎類型](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)