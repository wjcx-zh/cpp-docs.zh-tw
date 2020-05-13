---
title: 後置運算式
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 897eb80c713f786ecf0f7e6c9cf24cd8bdfc0aa8
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032274"
---
# <a name="postfix-expressions"></a>後置運算式

後置運算式包含主要運算式，或後置運算子後面接著主要運算式的運算式。 下表列出後置運算子。

### <a name="postfix-operators"></a>後置運算子

|運算子名稱|運算子標記法|
|-------------------|-----------------------|
|[副文稿運算子](../cpp/subscript-operator.md)|**[ ]**|
|[函式呼叫運算子](../cpp/function-call-operator-parens.md)|**( )**|
|[明確類型轉換運算子](../cpp/explicit-type-conversion-operator-parens.md)|*型態名稱***( )**|
|[成員存取運算子](../cpp/member-access-operators-dot-and.md)|**.** 或**->**|
|[後置遞增運算子](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[後置遞減運算子](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

下列語法描述可能的後置陳述式：

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

上面的*后修復表達式*可以是主表達式或其他後綴表達式。  請參考**主表示式**。  後置運算式由左至右分組，因此可讓運算式鏈結在一起，如下所示：

```cpp
func(1)->GetValue()++
```

在上面的運算式中,`func`是一個主運算`func(1)`式 ,是函數後綴表達`func(1)->GetValue`式, 是指定類成員的後綴`func(1)->GetValue()`表達式, 是另一個函數後綴表達式,整個表達式是遞修復表達式,遞增表達式,遞價表達式增加了 GetValue 的返回值。  整個運算式的意義是傳遞 1 做為呼叫 func 的引數，並取得類別的指標做為傳回值。  然後調用`GetValue()`該類,然後增加返回的值。

以上列出的運算式為指派運算式，表示這些運算式的結果必須是右值。

後置運算式格式

```cpp
simple-type-name ( expression-list )
```

表示建構函式的引動過程。  如果 simple-type-name 是一個基本類型，則運算式清單必須是單一運算式，而這個運算式表示將運算式的值轉型為基本類型。  此種轉型運算式會模擬建構函式。  由於這個格式允許使用相同的語法建構基本類型和類別，因此該格式在定義樣板類別時會特別有用。

*強制關鍵字*是**dynamic_cast、static_cast****static_cast**或**reinterpret_cast**之 一。  更多資訊可在**dynamic_cast、static_cast**與**static_cast****reinterpet_cast**中找到 。

**類型 id**運算符被視為後綴運算式。  請參考**型態化運算子**。

## <a name="formal-and-actual-arguments"></a>型式和實質引數

呼叫程式會利用「實質引數」將資訊傳遞至所呼叫的函式。 所呼叫的函式會使用對應的「型式引數」存取資訊。

呼叫函式時，會執行下列工作：

- 所有實質引數 (呼叫端所提供的引數) 都會進行評估。 這些引數並不需要遵循任何隱含的評估順序，但是會在所有引數都經過評估且所有副作用都已完成之後，才進入函式。

- 每個型式引數都會使用它在運算式清單中的對應實質引數初始化  (正式參數是在函數標頭中聲明並在函數正文中使用的參數。轉換就像透過初始化來完成一樣 - 在將實際參數轉換為正確的類型時,執行標準和使用者定義的轉換。 所執行的初始化將以下列程式碼提供概念上的說明：

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

   請注意，初始化的執行方式就如同使用等號語法，而不是括號語法。 將值傳遞至函式之前，會先製作 `i` 的複本  (關於詳細資訊,請參考[初始化器](../cpp/initializers.md)與[轉換](../cpp/user-defined-type-conversions-cpp.md)。

   因此,如果函數原型(聲明)調用類型**為長**的參數,並且調用程式提供**類型 int**的實際參數,則使用標準類型轉換將實際參數提升到**類型長**(請參閱[標準轉換](../cpp/standard-conversions.md))。

   提供沒有轉換成型式引數類型之標準或使用者定義轉換的實質引數是不正確的做法。

   對於類別類型的實質引數，型式引數會藉由呼叫類別的建構函式進行初始化。 (有關這些特殊類成員函數的更多,請參閱[建構函數](../cpp/constructors-cpp.md)。

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

當`func`從 main 調用時`param1`,正式`i`參數用`i`的值初始化(轉換為類型**長**,以對應於使用標準轉換的正確類型),`param2``j``j`並且用值 (使用標準轉換轉換為類型**雙**號)來初始化形式參數。

## <a name="treatment-of-argument-types"></a>引數類型的處理方式

宣告為 const 類型的正式引數無法在函式主體內變更。 函數可以更改任何不是類型**const**的參數。 但是,更改是函數的局部更改,不會影響實際參數的值,除非實際參數是對類型**const**物件的引用。

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

## <a name="ellipsis-and-default-arguments"></a>省略碼和預設參數

如需傳遞可變引數數目的詳細資訊只要使用下列兩種方法的其中一種，函式就可以宣告為接受比函式定義中所指定數目少的引數：省略符號 (`...`) 或預設引數。

橢圓表示可能需要參數,但聲明中未指定數字和類型。 一般來說，這並不是理想的 C++ 程式設計做法，因為它會失去其中一項 C++ 的優點：類型安全。 與已知形式參數類型和實際參數類型的函數相比,使用省略號聲明的函數的轉換不同:

- 如果實際參數為 **「浮點**」類型,則在函數調用之前將其提升為**雙**精度類型。

- 使用積分提升將任何已簽名或未簽名**的字元**、**短**字元、枚舉類型或位欄位轉換為已簽名或未簽名**的 int。**

- 任何類別類型的引數都會以傳值的方式做為資料結構傳遞，而複本會以二進位檔複製的方式建立，而不會以叫用類別之複製建構函式 (如果有的話) 的方式建立。

如果使用橢圓,則必須在參數清單中最後聲明。 有關傳遞可變參數數的詳細資訊,請參閱*運行時庫參考*中討論[va_arg、va_start和va_list。](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)

有關 CLR 程式設計中的預設參數的資訊,請參閱[變數參數清單 (...) (C++/CLI)。](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)

預設引數可讓您指定函式呼叫中未提供值時，引數應該假設的值。 下列程式碼片段將示範預設引數的運作方式。 有關指定預設參數的限制的詳細資訊,請參閱[預設參數](../cpp/default-arguments.md)。

```cpp
// expre_Ellipsis_and_Default_Arguments.cpp
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

上述程式會宣告接受兩個引數的函式 `print`。 但是,第二個參數*終止符*,`"\n"`具有預設值 。 在`main`中,前兩`print`個調用允許預設第二個參數提供新行以終止列印的字串。 第三個呼叫會為第二個引數指定明確的值。 程式的輸出為

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>另請參閱

[運算式的類型](../cpp/types-of-expressions.md)
