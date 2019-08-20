---
title: 標頭檔 (C++)
ms.date: 04/20/2018
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 98d37944f8c037f3ba25d80c7d35b3560ad11d40
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980478"
---
# <a name="header-files-c"></a>標頭檔 (C++)

程式元素的名稱，例如變數、函式、類別等等，必須先宣告才能使用。舉個例子，你在宣告 'x' 前不能只寫 `x = 42`。

```cpp
int x; // declaration
x = 42; // use x
```

「宣告」會告訴編譯器元素到底是 **int**、**double**、**函數**、**類別** 還是其他東西。此外，每個名稱必須要先在每個 .cpp 檔案（直接或間接）宣告後才能使用。當你編譯程式時，每個 .cpp 檔案皆會單獨編譯成一個編譯單元。編譯器不知道其他編譯單位所宣告的名稱，這意味著定義類別、函數或全域變數時，必須在每個使用該元素的額外 .cpp 檔中提供該元素的定義。每個檔案中的每個宣告必須完全相同。而當連結器嘗試將所有編譯單元合併成單一程式時，稍微不一致的宣告，都會引致錯誤或非預期的行為。

為了使潛在錯誤降到最低，C++ 就採納了使用 *標頭檔* 包含宣告的慣例。您會先在標頭檔宣告，然後在每個 .cpp 檔案或其他需要該宣告的標頭檔中使用 #include 指示詞。#include 指示詞會在編譯前，將標頭檔的副本直接插入每個 .cpp 檔案。

## <a name="example"></a>範例

下述例子列出了用於宣告類別，並於不同來源檔案中使用的常見方法。我們會從標頭檔：`my_class.h` 開始。它包含了類別定義，但注意，定義是不完整的；未定義 `do_something` 成員函數：

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

下一步，建立一個實作檔（通常使用 .cpp 或類似的副檔名）。我們會稱呼這個檔案為 my_class.cpp，並提供成員宣告的定義。我們為 `my_class.h` 檔案新增了一個 `#include` 指示詞，以便在 .cpp 檔案中的此處插入 my_class 的宣告。而後我們 include 了 `<iostream>` 以取得 `std::cout` 的宣告。請注意，當標頭檔跟來源檔存在相同目錄時，會使用引號，而角括弧則用於標準程式庫的標頭。此外，許多標準程式庫標頭不會有 .h 或其他任何檔案副檔名。

在實作檔中，我們可以選用 **using** 語句以避免需要使用「N::」或「std::」限定每個提及「my_class」或「cout」。不要在標頭檔中放入 **using** 語句！

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

現在我們可以在其他 .cpp 檔案使用 `my_class` 了。我們會 #include 標頭檔，以讓編譯器提取宣告。所有編譯器皆需要知道 my_class 是個類別，其包含一個稱之為 `do_something()` 的公用成員函式。

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

當編譯器完成將每個 .cpp 檔編譯成 .obj 檔案的程序後，它會將 .obj 檔案傳遞給連結器。當連結器合併物件檔案時，它會剛好找到一個 my_class 定義；其位於 my_class.cpp 產生的 .obj 檔中，而後編譯成功。

## <a name="include-guards"></a>Include 防護 (Include guard)

一般來說，標頭檔案會有 *include 防護* 或 `#pragma once` 指示詞，以確保它們不會被多次插入單一 .cpp 檔案中。

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>要放在標頭檔的內容

因為標頭檔可能會被包含在多個檔案內，因此它不能包含「可能產生多個相同名稱定義」的定義。下列所述是不允許，或被視為非常糟糕的作法：

- 命名空間或全域範圍的內建類型定義
- 非內嵌函數定義
- 非 const 變數定義
- 匯總定義
- 未命名的命名空間
- using 指示詞

使用 **using** 指示詞不一定會造成錯誤，但可能會因為它將命名空間帶入每個直接或間接包含該標頭檔的 .cpp 檔案作用域，而導致問題。

## <a name="sample-header-file"></a>標頭檔範例

以下範例列出了標頭檔所允許的各種宣告及定義種類：

```cpp
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```
