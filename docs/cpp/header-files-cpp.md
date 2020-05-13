---
title: 標題檔案 (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367237"
---
# <a name="header-files-c"></a>標題檔案 (C++)

在使用變數、函數、類等之前,必須聲明程式元素的名稱。 例如,不能只寫`x = 42`而不首先聲明"x"。

```cpp
int x; // declaration
x = 42; // use x
```

聲明告訴編譯器該元素是**int、****雙組**、**函數**、**類別**還是其他內容。  此外,必須在使用每個 .cpp 的檔中(直接或間接)聲明每個名稱。 編譯程式時,每個 .cpp 檔將獨立編譯為編譯單元。 編譯器不知道在其他編譯單元中聲明的名稱。 這意味著,如果定義類或函數或全域變數,則必須在使用它的每個附加 .cpp 檔中提供該事物的聲明。 該事物的每個聲明在所有檔中必須完全相同。 當連結器嘗試將所有編譯單元合併到單個程式中時,輕微的不一致將導致錯誤或意外行為。

為了將錯誤的可能性降至最低,C++採用了使用*標頭檔*來包含聲明的慣例。 在標頭檔中創建聲明,然後在每個 .cpp 檔或其他需要該聲明的標頭檔中使用#include指令。 #include指令在编译前将头文件的副本直接插入到 .cpp 檔中。

> [!NOTE]
> 在 Visual Studio 2019 中,C++20*模組*功能作為改進和最終替換頭檔引入。 有關詳細資訊,請參閱[C++ 中的模組概述](modules-cpp.md)。

## <a name="example"></a>範例

下面的示例顯示了一種聲明類,然後在其他源檔中使用它的常見方法。 我們將從頭文件開始。 `my_class.h` 它包含類定義,但請注意該定義不完整;未定義成員`do_something`函數:

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

接下來,創建一個實現檔(通常使用 .cpp 或類似擴展名)。 我們將調用檔my_class.cpp,並為成員聲明提供定義。 我們添加"my_class.h"檔的`#include`指令,以便將my_class聲明插入 .cpp 檔中的此時,並且我們`<iostream>``std::cout`包括在中拉取 聲明。 請注意,引號用於與源文件位於同一目錄中的標頭檔,角度括弧用於標準庫標頭。 此外,許多標準庫標頭沒有 .h 或任何其他文件擴展名。

在實現檔中,我們可以選擇使用**using**語句,以避免每次提及"my_class"或"cout"與"N::"或"std:"進行限定。  不要把**使用**語句放在你的頭檔中!

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

現在,我們可以在另`my_class`一個 .cpp 檔中使用。 我們#include頭檔,以便編譯器在聲明中提取。 編譯器需要知道的是,my_class是一個具有公共成員函數的類`do_something()`。

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

編譯器完成將每個 .cpp 檔案編譯到 .obj 檔中後,它將 .obj 檔傳遞給連結器。 當連結器合併物件檔時,它正好找到my_class一個定義;當鏈接器合併物件檔時,它將找到一個定義,用於my_class。它位於為 my_class.cpp 生成的 .obj 檔中,生成成功。

## <a name="include-guards"></a>包括護衛

通常,標頭檔具有*包含防護*或`#pragma once`指令,以確保它們不會多次插入到單個 .cpp 檔中。

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

## <a name="what-to-put-in-a-header-file"></a>在標頭檔中放入什麼

由於頭檔可能由多個檔包含,因此它不能包含可能產生同名多個定義的定義。 不允許使用以下操作,或被視為非常糟糕的做法:

- 命名空間或全域範圍的內建型態定義
- 非內聯函數定義
- 非同義變數定義
- 彙總定義
- 未命名的命名空間
- using 指示詞

**使用 using**指令不一定會導致錯誤,但可能會導致問題,因為它會將命名空間引入直接或間接包含該標頭的每個 .cpp 檔中的範圍。

## <a name="sample-header-file"></a>範例標頭檔

下面的範例顯示標頭檔中允許的各種聲明和定義:

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
