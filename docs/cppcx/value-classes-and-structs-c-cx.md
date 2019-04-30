---
title: 實值類別與結構 (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 5b9b50ba7200439e9ce648c53d52ce37226f61d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384981"
---
# <a name="value-classes-and-structs-ccx"></a>實值類別與結構 (C++/CX)

A*實值結構*或是*的實值類別*是 Windows 執行階段相容的 POD （「 一般舊資料結構 」）。 具有固定的大小，且只包含欄位；不同於 ref 類別，此類別沒有屬性。

下列範例示範如何宣告和初始化實值結構。

```

// in mainpage.xaml.h:
    value struct TestStruct
    {
        Platform::String^ str;
        int i;
    };

    value struct TestStruct2
    {
        TestStruct ts;
        Platform::String^ str;
        int i;
    };

// in mainpage.cpp:
    // Initialize a value struct with an int and String
    TestStruct ts = {"I am a TestStruct", 1};

    // Initialize a value struct that contains
    // another value struct, an int and a String
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};

    // Initialize value struct members individually.
    TestStruct ts3;
    ts3.i = 108;
    ts3.str = "Another way to init a value struct.";
```

當實值類型的變數指派給另一個變數時，值會被複製，使這兩個變數都具有各自的資料複本。 「 *值結構* 」(Value Struct) 是一種大小固定的結構，會透過 `value struct` 關鍵字進行宣告，且僅包含公用資料欄位。

「 *實值類別* 」(Value Class) 與 `value struct` 類似，差別在於其欄位必須明確指定為公用存取範圍。 其宣告可透過 `value class` 關鍵字來執行。

實值結構或實值類別可以包含基本數值型别、 列舉類別的欄位`Platform::String^`，或[platform:: ibox \<T > ^](../cppcx/platform-ibox-interface.md)其中 T 是數值類型或列舉類別或實值類別或結構。 `IBox<T>^` 欄位可以有 `nullptr`值，這是 C++ 實作「 *可為 Null 的實值類型*」(Nullable Value Type) 這個概念的方式。

包含 `Platform::String^` 或 `IBox<T>^` 類型做為成員的實值類別或實值結構，不具備 `memcpy`功能。

由於 `value class` 或 `value struct` 的所有成員都是公用成員，且會發出至中繼資料，因此不允許標準 C++ 類型做為成員。 這與 ref 類別不同，ref 類別可以包含 `private` 或 `internal` 標準 C++ 類型。

下列程式碼片段會將 `Coordinates` 和 `City` 型別宣告為值結構。 請注意，其中一個 `City` 資料成員是 `GeoCoordinates` 型別。 `value struct` 可包含其他實值結構做為成員。

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>參數傳遞以取得實值類型

如果您有作為函式或方法參數的實值類型，它通常依值傳遞。 對於較大的物件，這會造成效能問題。 在 Visual Studio2013 和舊版中，C++/CX 中的實值類型永遠依值傳遞。 在 Visual Studio 2015 及更新的版本中，您可依參考或值傳遞實值類型。

若要宣告依值傳遞實值類型的參數，請使用下列程式碼：

```
void Method1(MyValueType obj);
```

若要宣告依參考傳遞實值類型的參數，請使用參考符號 (&)，如下所示：

```
void Method2(MyValueType& obj);
```

Method2 內的類型是 MyValueType 的參考，工作方式與 Standard C++ 的參考類型相同。

當您從另一種語言 (例如 C#) 呼叫 Method1 時，不必使用 `ref` 或 `out` 關鍵字。 呼叫 Method2 時，請使用 `ref` 關鍵字。

```
Method2(ref obj);
```

您也可以使用指標符號 (*) 依參考傳遞實值類型。 對其他語言中的呼叫端而言，行為是相同的 (呼叫端在 C# 使用 `ref` 關鍵字)，但在方法中，類型對實值類型就是個指標。

## <a name="nullable-value-types"></a>可為 Null 的實值型別

如先前所述，實值類別或實值結構可以具有類型的欄位[platform:: ibox\<T > ^](../cppcx/platform-ibox-interface.md)— 比方說， `IBox<int>^`。 這類欄位可以有 `int` 類型的任何有效數值，也可以有 `nullptr`值。 您可以將可為 null 的欄位當做引數傳遞至其參數宣告為選擇性的方法，或傳遞至實值型別不需要有值的其他地方。

下列範例會示範如何初始化具有可為 Null 之欄位的結構。

```
public value struct Student
{
    Platform::String^ Name;
    int EnrollmentYear;
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.
};
//To create a Student struct, one must populate the nullable type.
MainPage::MainPage()
{
    InitializeComponent();

    Student A;
    A.Name = "Alice";
    A.EnrollmentYear = 2008;
    A.GraduationYear = ref new Platform::Box<int>(2012);

    Student B;
    B.Name = "Bob";
    B.EnrollmentYear = 2011;
    B.GraduationYear = nullptr;

    IsCurrentlyEnrolled(A);
    IsCurrentlyEnrolled(B);
}
bool MainPage::IsCurrentlyEnrolled(Student s)
{
    if (s.GraduationYear == nullptr)
    {
        return true;
    }
    return false;
}
```

實值結構本身可以透過相同方式成為可為 Null 的結構，如下所示：

```

public value struct MyStruct
{
public:
    int i;
    Platform::String^ s;
};

public ref class MyClass sealed
{
public:
    property Platform::IBox<MyStruct>^ myNullableStruct;
};
```

## <a name="see-also"></a>另請參閱

[類型系統 (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[視覺化C++語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)<br/>
[Ref 類別與結構 (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
