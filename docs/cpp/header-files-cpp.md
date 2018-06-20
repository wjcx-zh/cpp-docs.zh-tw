---
title: 標頭檔 （c + +） |Microsoft 文件
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
ms.openlocfilehash: b571cd2836e66ebef21898af27cf2a6d7082e0e5
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36261044"
---
# <a name="header-files-c"></a>標頭檔 （c + +）

必須宣告程式項目，例如變數、 函式、 類別和等等的名稱，然後才能使用。 例如，您就無法寫入`x = 42`未宣告 'x'。 

```cpp
int x; // declaration
x = 42; // use x
```

 宣告告知編譯器是否會**int**、 **double**、**函式**、**類別**或其他項目。  此外，每個名稱必須宣告 （直接或間接） 在每個.cpp 檔案中使用它。 當您編譯程式時，每個.cpp 檔案會單獨編譯成編譯單位。 編譯器不了解哪些名稱在其他編譯單位中宣告。 這表示，如果您定義類別或函式或全域變數，您必須提供該動作，它會使用每個額外的.cpp 檔案中的宣告。 該動作的每個宣告中的所有檔案必須完全相同。 稍微不一致的問題會導致錯誤或非預期的行為，當連結器會嘗試合併到單一程式的所有編譯單位。

錯誤的可能性降到最低，c + + 已採用使用的慣例*標頭檔*包含宣告。 標頭檔中進行宣告，然後使用 #include 指示詞在每個.cpp 檔案中，或其他標頭檔需要的宣告。 #Include 指示詞插入一份標頭檔直接在編譯之前的.cpp 檔案。 

## <a name="example"></a>範例

下列範例宣告類別並將它用於不同原始程式檔的常見方式。 我們將開始標頭檔， **my_class.h**。 它包含的類別定義，但請注意該定義是不完整。成員函式`do_something`未定義：

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

接下來，建立實作檔 （通常以.cpp 或類似的擴充功能）。 我們會呼叫檔案 my_class.cpp，並提供成員宣告的定義。 我們加入`#include`指示詞"my_class.h 」 檔案，才能插入 my_class 宣告此時在.cpp 檔案，及我們包含 **\<iostream >** 的宣告中提取`std::cout`。 請注意，在原始程式檔，與相同的目錄中的標頭檔使用雙引號，標準程式庫標頭會使用角括號。 此外，許多標準的程式庫標頭沒有.h 或任何其他副檔名。

在實作檔案中，我們可以選擇性地使用**使用**陳述式，以避免來限定每提及"my_class"或"cout"與"n::"或"std::"。  不要放置**使用**標頭檔中的陳述式 ！

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

現在我們可以使用`my_class`另一個的.cpp 檔案中。 我們 #include 的標頭檔，如此，編譯器會在宣告中提取。 所有編譯器必須知道是該 my_class 具有呼叫公用成員函式的類別， `do_something()`。

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

編譯器編譯為.obj 檔案的每個.cpp 檔案之後，它會將.obj 檔傳遞至連結器中。 當連結器會合併物件檔案找到一個定義 my_class;它是個 my_class.cpp，產生.obj 檔案中，並建置成功。

## <a name="include-guards"></a>Include 防護

標頭檔通常需要*include 防護*或 **#pragma 一次**指示詞，以確保它們不會插入多次到單一的.cpp 檔案。 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>ifndef MY_CLASS_H / / include 防護
#<a name="define-myclassh"></a>定義 MY_CLASS_H


命名空間 N {類別 my_class {公用： void do_something();};

}

#<a name="endif--myclassh-"></a>endif / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>標頭檔中放入什麼

標頭檔潛在可能包含由多個檔案，因為它不能包含可能會產生具有相同名稱的多個定義的定義。 下列不允許，或是會視為非常不良作法：

- 在命名空間或全域範圍的內建型別定義
- 非內嵌函式定義 
- 非 const 變數定義
- 彙總的定義
- 未命名的命名空間
- using 指示詞

使用**使用**指示詞將不一定會產生錯誤，但因為命名空間帶入範圍中直接或間接包含該標頭的每個.cpp 檔案，則可能會造成問題。 

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
