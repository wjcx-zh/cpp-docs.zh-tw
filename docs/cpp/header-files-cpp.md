---
title: 標頭檔（c + +）
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 0b76773b8b7d55645c807588fe41b242df9eea2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227448"
---
# <a name="header-files-c"></a>標頭檔（c + +）

程式元素的名稱（例如變數、函式、類別等等）必須先經過宣告，才能使用。 例如，您不能只在 `x = 42` 未先宣告 ' x ' 的情況下進行寫入。

```cpp
int x; // declaration
x = 42; // use x
```

宣告會告訴編譯器元素是 **`int`** 、a、函式 **`double`** **function** **`class`** 或其他專案。  此外，每個名稱都必須在使用它的每個 .cpp 檔案中宣告（直接或間接）。 當您編譯器時，每個 .cpp 檔案都會單獨編譯成一個編譯單位。 編譯器不知道在其他編譯單位中宣告的名稱。 這表示，如果您定義了類別或函式或全域變數，就必須在使用它的每個額外 .cpp 檔案中，提供該內容的宣告。 在所有檔案中，該內容的每個宣告必須完全相同。 當連結器嘗試將所有編譯單元合併成單一程式時，稍微不一致會導致錯誤或非預期的行為。

為了將錯誤的可能性降到最低，c + + 已採用使用*標頭檔*來包含宣告的慣例。 您會在標頭檔中進行宣告，然後在每個 .cpp 檔案或其他需要該宣告的標頭檔中使用 #include 指示詞。 #Include 指示詞會在編譯之前，直接在 .cpp 檔案中插入標頭檔的複本。

> [!NOTE]
> 在 Visual Studio 2019 中，c + + 20*模組*功能是針對標頭檔的改進和最終取代而引進的。 如需詳細資訊，請參閱[c + + 中的模組總覽](modules-cpp.md)。

## <a name="example"></a>範例

下列範例顯示宣告類別，然後在不同的原始檔中使用它的常見方式。 我們會從標頭檔開始 `my_class.h` 。 它包含類別定義，但請注意，定義不完整;未定義成員函式 `do_something` ：

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

接下來，建立一個執行檔（通常使用 .cpp 或類似的副檔名）。 我們將會呼叫檔案 my_class .cpp，並提供成員宣告的定義。 我們會新增 "my_class .h" 檔案的指示詞，以便在 .cpp 檔案中 `#include` 的這個點插入 my_class 宣告，而且我們 `<iostream>` 要包含以提取的宣告 `std::cout` 。 請注意，引號會用於與原始程式檔位於相同目錄中的標頭檔，而角括弧則用於標準程式庫標頭。 此外，許多標準程式庫標頭並沒有 .h 或任何其他副檔名。

在執行檔案中，我們可以選擇性地使用 **`using`** 語句，以避免必須以 "N：：" 或 "std：：" 的每個提及 "my_class" 或 "cout" 的資格。  不要將 **`using`** 語句放在標頭檔中！

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

現在我們可以 `my_class` 在另一個 .cpp 檔案中使用。 我們 #include 標頭檔，讓編譯器提取宣告。 所有編譯器都必須知道，my_class 是具有稱為公用成員函式的類別 `do_something()` 。

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

在編譯器完成將每個 .cpp 檔案編譯成 .obj 檔案之後，它會將 .obj 檔案傳遞至連結器。 當連結器合併物件檔案時，它只會找到一個 my_class 的定義;它位於為 my_class .cpp 產生的 .obj 檔案中，而組建成功。

## <a name="include-guards"></a>包含防護

標頭檔通常會有*include 防護*或指示詞， `#pragma once` 以確保它們不會多次插入單一 .cpp 檔案中。

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

## <a name="what-to-put-in-a-header-file"></a>要放在標頭檔中的內容

由於標頭檔可能會包含在多個檔案中，因此它不能包含可能會產生多個相同名稱定義的定義。 下列是不允許的，或被視為非常不好的作法：

- 命名空間或全域範圍中的內建類型定義
- 非內嵌函式定義
- 非 const 變數定義
- 匯總定義
- 未命名的命名空間
- using 指示詞

使用指示詞 **`using`** 不一定會導致錯誤，但可能會造成問題，因為它會將命名空間帶入每個 .cpp 檔案中直接或間接包含該標頭的範圍。

## <a name="sample-header-file"></a>範例標頭檔

下列範例顯示標頭檔中允許的各種宣告和定義類型：

```cpp
// sample.h
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
