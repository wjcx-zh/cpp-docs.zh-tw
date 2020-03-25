---
title: 後置運算式
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 25dfc6fd8f28f6c78fd5a4e9f76759ac076cae1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177686"
---
# <a name="postfix-expressions"></a>後置運算式

後置運算式包含主要運算式，或後置運算子後面接著主要運算式的運算式。 下表列出後置運算子。

### <a name="postfix-operators"></a>後置運算子

|運算子名稱|運算子標記法|
|-------------------|-----------------------|
|[注標運算子](../cpp/subscript-operator.md)|**[ ]**|
|[函式呼叫運算子](../cpp/function-call-operator-parens.md)|**( )**|
|[明確類型轉換運算子](../cpp/explicit-type-conversion-operator-parens.md)|*類型名稱* **（）**|
|[成員存取運算子](../cpp/member-access-operators-dot-and.md)|**。** 或 **->**|
|[後置遞增運算子](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[後置遞減運算子](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

下列語法描述可能的後置陳述式：

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

以上的後置*運算式*可能是主要運算式或另一個後置運算式。  請參閱**主要運算式**。  後置運算式由左至右分組，因此可讓運算式鏈結在一起，如下所示：

```cpp
func(1)->GetValue()++
```

在上述運算式中，`func` 是一個主要運算式，`func(1)` 是函式後置運算式，則 `func(1)->GetValue` 是指定類別成員的後置運算式，`func(1)->GetValue()` 是另一個函式後置運算式，而整個運算式為後置運算式遞增 GetValue 的傳回值。  整個運算式的意義是傳遞 1 做為呼叫 func 的引數，並取得類別的指標做為傳回值。  然後在該類別上呼叫 `GetValue()`，然後遞增傳回的值。

以上列出的運算式為指派運算式，表示這些運算式的結果必須是右值。

後置運算式格式

```cpp
simple-type-name ( expression-list )
```

表示建構函式的引動過程。  如果 simple-type-name 是一個基本類型，則運算式清單必須是單一運算式，而這個運算式表示將運算式的值轉型為基本類型。  此種轉型運算式會模擬建構函式。  由於這個格式允許使用相同的語法建構基本類型和類別，因此該格式在定義樣板類別時會特別有用。

*Cast-關鍵字*是**dynamic_cast**、 **static_cast**或**reinterpret_cast**的其中一個。  如需詳細資訊，請參閱**dynamic_cast**、 **static_cast**和**reinterpet_cast**。

**Typeid**運算子會被視為後置運算式。  請參閱**typeid 運算子**。

## <a name="formal-and-actual-arguments"></a>型式和實質引數

呼叫程式會利用「實質引數」將資訊傳遞至所呼叫的函式。 所呼叫的函式會使用對應的「型式引數」存取資訊。

呼叫函式時，會執行下列工作：

- 所有實質引數 (呼叫端所提供的引數) 都會進行評估。 這些引數並不需要遵循任何隱含的評估順序，但是會在所有引數都經過評估且所有副作用都已完成之後，才進入函式。

- 每個型式引數都會使用它在運算式清單中的對應實質引數初始化 （型式引數是在函式標頭中宣告並在函式主體中使用的引數）。轉換的完成方式就如同初始化一樣，在將實際引數轉換成正確的型別時，也會執行標準和使用者定義的轉換。 所執行的初始化將以下列程式碼提供概念上的說明：

    ```cpp
    void Func( int i ); // Function prototype
    ...
    Func( 7 );          // Execute function call
    ```

   呼叫之前的概念初始化為：

    ```cpp
    int Temp_i = 7;
    Func( Temp_i );
    ```

   請注意，初始化的執行方式就如同使用等號語法，而不是括號語法。 將值傳遞至函式之前，會先製作 `i` 的複本 （如需詳細資訊，請參閱[初始化運算式](../cpp/initializers.md)和[轉換](../cpp/user-defined-type-conversions-cpp.md)）。

   因此，如果函式原型（宣告）呼叫**long**類型的引數，而且呼叫程式提供**int**類型的實質引數，則會使用標準類型轉換來將實際引數提升為**Long**類型（請參閱[標準轉換](../cpp/standard-conversions.md)）。

   提供沒有轉換成型式引數類型之標準或使用者定義轉換的實質引數是不正確的做法。

   對於類別類型的實質引數，型式引數會藉由呼叫類別的建構函式進行初始化。 （如需這些特殊類別成員函式的詳細[資訊，請](../cpp/constructors-cpp.md)參閱函式）。

- 函式呼叫將會執行。

下列程式片段將示範函式呼叫：

```cpp
// expre_Formal_and_Actual_Arguments.cpp
void func( long param1, double param2 );

int main()
{
    long i = 1;
    double j = 2;

    // Call func with actual arguments i and j.
    func( i, j );
}

// Define func with formal parameters param1 and param2.
void func( long param1, double param2 )
{
}
```

從 main 呼叫 `func` 時，會使用 `i` 的值來初始化正式參數 `param1` （`i` 會轉換成**long**類型，以使用標準轉換來對應到正確的類型），而正式參數 `param2` 會使用 `j` 的值進行初始化（`j` 會使用標準轉換來轉換為**double**類型）。

## <a name="treatment-of-argument-types"></a>引數類型的處理方式

宣告為 const 類型的正式引數無法在函式主體內變更。 函數可以變更任何不是**const**類型的引數。 不過，這項變更對函式而言是本機的，而且不會影響實際引數的值，除非實際的引數是不是**const**類型之物件的參考。

下列函式將說明一些這類概念：

```cpp
// expre_Treatment_of_Argument_Types.cpp
int func1( const int i, int j, char *c ) {
   i = 7;   // C3892 i is const.
   j = i;   // value of j is lost at return
   *c = 'a' + j;   // changes value of c in calling function
   return i;
}

double& func2( double& d, const char *c ) {
   d = 14.387;   // changes value of d in calling function.
   *c = 'a';   // C3892 c is a pointer to a const object.
    return d;
}
```

## <a name="ellipses-and-default-arguments"></a>省略符號和預設引數

如需傳遞可變引數數目的詳細資訊只要使用下列兩種方法的其中一種，函式就可以宣告為接受比函式定義中所指定數目少的引數：省略符號 (`...`) 或預設引數。

省略符號表示可能需要引數，但是宣告中未指定數目和類型。 一般來說，這並不是理想的 C++ 程式設計做法，因為它會失去其中一項 C++ 的優點：類型安全。 以省略符號宣告的函式適用的轉換方式，與已知正式和實質引數類型的函式所適用的轉換方式不同：

- 如果實際引數的類型為**float**，則會在函式呼叫之前提升為**double**類型。

- 任何帶正負號或不帶正負號的**char**、 **short**、列舉類型或位欄位都會使用整數提升轉換成帶正負號或不帶正負號的**int** 。

- 任何類別類型的引數都會以傳值的方式做為資料結構傳遞，而複本會以二進位檔複製的方式建立，而不會以叫用類別之複製建構函式 (如果有的話) 的方式建立。

若使用省略符號，則必須是引數清單中最後宣告的項目。 如需傳遞可變引數數目的詳細資訊，請參閱《*執行時間程式庫參考*》中[va_arg、va_start 和 va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)的討論。

如需 CLR 程式設計中預設引數的詳細資訊，請參閱[Variable 引數清單C++（...）（/cli）](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)。

預設引數可讓您指定函式呼叫中未提供值時，引數應該假設的值。 下列程式碼片段將示範預設引數的運作方式。 如需有關指定預設引數之限制的詳細資訊，請參閱[預設引數](../cpp/default-arguments.md)。

```cpp
// expre_Ellipses_and_Default_Arguments.cpp
// compile with: /EHsc
#include <iostream>

// Declare the function print that prints a string,
// then a terminator.
void print( const char *string,
            const char *terminator = "\n" );

int main()
{
    print( "hello," );
    print( "world!" );

    print( "good morning", ", " );
    print( "sunshine." );
}

using namespace std;
// Define print.
void print( const char *string, const char *terminator )
{
    if( string != NULL )
        cout << string;

    if( terminator != NULL )
        cout << terminator;
}
```

上述程式會宣告接受兩個引數的函式 `print`。 不過，第二個引數（*結束字元*）有預設值 `"\n"`。 在 `main`中，`print` 的前兩個呼叫允許預設的第二個引數，以提供新的行來結束列印的字串。 第三個呼叫會為第二個引數指定明確的值。 程式的輸出為

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>另請參閱

[運算式的類型](../cpp/types-of-expressions.md)
