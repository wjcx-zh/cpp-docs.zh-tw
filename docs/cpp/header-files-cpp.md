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

程式元素的名稱 (例如變數、函式、類別等等) 必須先宣告才能使用。 例如，若未先宣告 'x'，不能寫 `x = 42`。

```cpp
int x; // declaration
x = 42; // use x
```

宣告會告訴編譯器元素是**int**、 **double**、函式、**類別**或其他專案。  此外, 每個名稱都必須在使用它的每個 .cpp 檔案中宣告 (直接或間接)。 當您編譯器時, 每個 .cpp 檔案都會單獨編譯成一個編譯單位。 編譯器不知道在其他編譯單位中宣告的名稱。 這表示, 如果您定義了類別或函式或全域變數, 就必須在使用它的每個額外 .cpp 檔案中, 提供該內容的宣告。 在所有檔案中, 該內容的每個宣告必須完全相同。 當連結器嘗試將所有編譯單元合併成單一程式時, 稍微不一致會導致錯誤或非預期的行為。

為了將錯誤的可能性降到C++最低, 已採用使用*標頭檔*來包含宣告的慣例。 您會在標頭檔中進行宣告, 然後在每個 .cpp 檔案或其他需要該宣告的標頭檔中使用 #include 指示詞。 #Include 指示詞會在編譯之前, 直接在 .cpp 檔案中插入標頭檔的複本。

## <a name="example"></a>範例

下列範例顯示宣告類別, 然後在不同的原始檔中使用它的常見方式。 我們會從標頭檔`my_class.h`開始。 它包含類別定義, 但請注意, 定義不完整;未定義成員`do_something`函式:

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

接下來, 建立一個執行檔 (通常使用 .cpp 或類似的副檔名)。 我們會呼叫 my_class 檔案, 並提供成員宣告的定義。 我們會新增`#include` "my_class" 檔案的指示詞, 以便在 .cpp 檔案中的這個點插入 my_class 宣告, 而且我們要包含`<iostream>`以`std::cout`提取的宣告。 請注意, 引號會用於與原始程式檔位於相同目錄中的標頭檔, 而角括弧則用於標準程式庫標頭。 此外, 許多標準程式庫標頭並沒有 .h 或任何其他副檔名。

在執行檔案中, 我們可以選擇性地使用**using**語句, 以避免必須以 "N::" 或 "std::" 來限定每個提及 "my_class" 或 "cout"。  不要在標頭檔中放入**using**語句!

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

現在我們可以在`my_class`另一個 .cpp 檔案中使用。 我們 #include 標頭檔, 讓編譯器提取宣告。 所有編譯器都必須知道, my_class 是具有稱為`do_something()`公用成員函式的類別。

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

在編譯器完成將每個 .cpp 檔案編譯成 .obj 檔案之後, 它會將 .obj 檔案傳遞至連結器。 當連結器合併物件檔案時, 它只會找到一個 my_class 的定義;它位於為 my_class 產生的 .obj 檔案中, 且組建成功。

## <a name="include-guards"></a>包含防護

標頭檔通常會有*include 防護*或`#pragma once`指示詞, 以確保它們不會多次插入單一 .cpp 檔案中。

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

由於標頭檔可能會包含在多個檔案中, 因此它不能包含可能會產生多個相同名稱定義的定義。 下列是不允許的, 或被視為非常不好的作法:

- 命名空間或全域範圍中的內建類型定義
- 非內嵌函式定義
- 非 const 變數定義
- 匯總定義
- 未命名的命名空間
- using 指示詞

**Using**指示詞的使用不一定會造成錯誤, 但是可能會造成問題, 因為它會將命名空間帶入每個 .cpp 檔案中直接或間接包含該標頭的範圍。

## <a name="sample-header-file"></a>範例標頭檔

下列範例顯示標頭檔中允許的各種宣告和定義類型:

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
