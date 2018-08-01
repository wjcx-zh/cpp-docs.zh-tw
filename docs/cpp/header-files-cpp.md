---
title: 標頭檔 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- header files [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f6950049d9bd9b9264383ab6e5e216023526880
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404761"
---
# <a name="header-files-c"></a>標頭檔 （c + +）

必須宣告程式項目，例如變數、 函式、 類別和等等的名稱，才能使用。 例如，您就無法寫入`x = 42`未宣告 'x'。 

```cpp
int x; // declaration
x = 42; // use x
```

 宣告會告知編譯器是否是**int**、 **double**，則**函式**、**類別**或一些其他的事。  此外，每個名稱必須宣告 （直接或間接） 中使用每個.cpp 檔案中。 當您編譯程式時，每個.cpp 檔案會單獨編譯至編譯單位。 編譯器並不知道哪些名稱宣告在其他的編譯單位中。 這表示，如果您定義類別或函式或全域變數，您必須提供的話，那會使用它的每個額外的.cpp 檔案的宣告。 該動作的每個宣告中的所有檔案必須完全相同。 稍微不一致的問題會導致錯誤或非預期的行為，當連結器嘗試合併到單一程式中的所有編譯單位。

錯誤的可能性降到最低，c + + 已採用的慣例*標頭檔*包含宣告。 您在 標頭檔中進行宣告，然後使用 #include 指示詞中的每個.cpp 檔案，或其他標頭檔所需的宣告。 #Include 指示詞插入標頭檔的複本直接在編譯之前的.cpp 檔案。 

## <a name="example"></a>範例

下列範例示範宣告類別，並將它用於不同原始程式檔的常見方式。 我們將開始標頭檔， `my_class.h`。 它包含類別定義，但請注意，定義不完整。此成員函式`do_something`未定義：

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

接下來，建立實作檔 （通常使用.cpp 或類似的延伸模組）。 我們將呼叫檔案 my_class.cpp，並提供成員宣告的定義。 我們會新增`#include`指示詞 」 my_class.h"檔案，以有插入 my_class 宣告目前在.cpp 檔案，以及我們包含`<iostream>`提取的宣告中`std::cout`。 請注意，在與原始程式檔中，相同的目錄中的標頭檔使用雙引號角括號會用於標準程式庫標頭。 此外，許多標準的程式庫標頭並沒有.h 或任何其他副檔名。

在實作檔案中，我們可以選擇性地使用**使用**陳述式，以避免限定每個提到的 「 my_class"或"cout"與"n::"或"std::"。  不要將放**使用**標頭檔中的陳述式 ！

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

現在我們可以使用`my_class`另一個的.cpp 檔案中。 我們 #include 標頭檔，讓編譯器會在宣告中提取。 所有編譯器必須知道是該 my_class 類別具有公用成員函式呼叫`do_something()`。

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

編譯器完成編譯為.obj 檔案的每個.cpp 檔案之後，它會傳遞.obj 檔給連結器。 當連結器合併物件檔案找到一個定義 my_class;它是個 my_class.cpp，產生的.obj 檔案中，並建置成功。

## <a name="include-guards"></a>Include 防護

一般而言，標頭檔都有*include 防護*或`#pragma once`指示詞，以確保它們不會插入多次成單一的.cpp 檔案。 

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

## <a name="what-to-put-in-a-header-file"></a>標頭檔中放入什麼

多個檔案可能會有可能包含標頭檔，因為它不能包含可能會產生具有相同名稱的多個定義的定義。 下列不允許，或視為非常適合：

- 在命名空間或全域範圍的內建的類型定義
- 非內嵌函式定義 
- 非 const 變數的定義
- 彙總的定義
- 未命名的命名空間
- using 指示詞

利用**使用**指示詞不一定會發生錯誤，但可能造成問題，因為它的命名空間帶入範圍中直接或間接包含該標頭的每個.cpp 檔案。 

## <a name="sample-header-file"></a>範例標頭檔

下列範例顯示各種宣告和定義的標頭檔中允許的：

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