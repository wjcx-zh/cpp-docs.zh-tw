---
title: 函式多載
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: 0eaaf5c8fd18d4d00652107a5a2071b2f5774d7c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232309"
---
# <a name="function-overloading"></a>函式多載

C++ 允許在相同範圍內指定多個同名的函式。 這些*函數稱為多*載函式。 多載函式可讓您針對函式提供不同的語義，視引數的類型和數目而定。

例如， `print` 接受引數的函式 `std::string` 可能會執行非常不同的工作，而不是採用類型之引數的作業 **`double`** 。 多載可讓您不需要使用或之類的名稱 `print_string` `print_double` 。 在編譯時期，編譯器會根據呼叫者傳入的引數類型，選擇要使用的多載。  如果您呼叫 `print(42.0)` ，則會叫用函式 `void print(double d)` 。 如果您呼叫 `print("hello world")` ，則會叫用多載 `void print(std::string)` 。

您可以多載成員函式和非成員函式。 下表將說明 C++ 使用函式宣告的哪些部分區分在相同範圍內具有相同名稱的函式群組。

### <a name="overloading-considerations"></a>多載考量

|函式宣告項目|是否用於多載？|
|----------------------------------|---------------------------|
|函式傳回類型|否|
|引數數目|是|
|引數類型|是|
|省略符號是否存在|是|
|名稱的使用 **`typedef`**|否|
|未指定的陣列範圍|否|
|**`const`** 或**`volatile`**|是，適用于整個函式|
|[Ref 限定詞](#ref-qualifiers)|是|

## <a name="example"></a>範例

下列範例將示範如何使用多載。

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

上述程式碼示範檔案範圍中 `print` 函式的多載。

預設引數不會視為函式類型的一部分。 因此，它不會用於選取多載函式。 兩個函式的不同之處只有在其預設引數是視為多重定義而不是多載函式。

無法為多載運算子提供預設引數。

## <a name="argument-matching"></a>引數對應

多載函式會在為了找出目前範圍中最符合函式呼叫所提供引數的函式宣告項目時選取。 如果找到適合的函式，就會呼叫該函式。 在此內容中，「適合」的意義是：

- 找到完全相符項目。

- 已執行一般轉換。

- 已執行整數提升。

- 有轉換成所需引數類型的標準轉換存在。

- 有轉換成所需引數類型的使用者定義轉換 (轉換運算子或建構函式) 存在。

- 找到省略符號所表示的引數。

編譯器會為每一個引數建立一組候選函式。 候選函式是指函式中該位置的實際引數可以轉換成正式引數的類型。

每個引數都會有一組建置的「最相符函式」，而且選取的函式是所有集合的交集。 如果交集包含多個函式，則多載會變得模稜兩可並產生錯誤。 最後選取的函式對於至少一個引數來說，永遠是比群組中其他每一個函式更理想的相符項目。 如果沒有明顯的優勝者，函式呼叫會產生錯誤。

以下列宣告為例 (在下面的討論中，函式會標記為 `Variant 1`、`Variant 2` 和 `Variant 3` 以便識別)：

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

以下列陳述式為例：

```cpp
F1 = Add( F2, 23 );
```

上面的陳述式會建置兩個集合：

|集合 1：第一個引數為 Fraction 類型的候選函式|Set 2：第二個引數可以轉換成類型的候選函式**`int`**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Variant 1|Variant 1 （ **`int`** 可以 **`long`** 使用標準轉換轉換成）|
|Variant 3||

Set 2 中的函式是指有從實際的參數類型隱含轉換成正式參數類型的函數，而在這類函數中，有一個函數可將實際參數類型轉換成其型式參數類型的「成本」為最小值。

這兩個集合的交集為 Variant 1。 模稜兩可函式呼叫的範例如下：

```cpp
F1 = Add( 3, 6 );
```

上述函式呼叫會建立下列集合：

|Set 1：具有類型之第一個引數的候選函式**`int`**|Set 2：具有類型之第二個引數的候選函式**`int`**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Variant 2 （ **`int`** 可以 **`long`** 使用標準轉換轉換成）|Variant 1 （ **`int`** 可以 **`long`** 使用標準轉換轉換成）|

因為這兩個集合的交集是空的，所以編譯器會產生錯誤訊息。

針對引數比對，具有*n*個預設引數的函式會被視為*n*+ 1 個不同的函式，每個函數都有不同數目的引數。

省略符號 (...) 做為萬用字元使用，它會比對任何實質引數。 如果您不想要特別小心設計多載函式集合，它可能會導致許多不明確的集合。

> [!NOTE]
> 在遇到函式呼叫之前，無法判斷多載函式的不明確。 遇到函式呼叫時，會為函式呼叫中的每個引數建置集合，如此就可以判斷是否有明確的多載存在。 這表示，模稜兩可的情況可能會持續存在程式碼中，直到特定函式呼叫撤銷這些情況為止。

## <a name="argument-type-differences"></a>引數類型差異

多載函式會區分採用不同初始設定式的各種引數類型。 因此，做為多載的用途時，特定類型的引數以及該類型的參考都會視為相同。 因為它們會採用相同的初始設定式，所以會將它們視為相同。 例如，`max( double, double )` 與 `max( double &, double & )` 會視為相同。 同時宣告兩個這類函式會產生錯誤。

基於相同的原因，或所修改之類型的函式引數，其 **`const`** **`volatile`** 處理方式不會與多載用途的基底類型不同。

不過，函式多載機制可以區別由和所限定的 **`const`** 參考 **`volatile`** ，以及基底類型的參考。 它可以讓程式碼如下：

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>輸出

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

**`const`** 和物件的指標 **`volatile`** 也會視為與多載用途的基底類型指標不同。

## <a name="argument-matching-and-conversions"></a>引數比對和轉換

當編譯器嘗試比對實質引數與函式宣告中的引數時，如果找不到完全相符的項目，它可以提供取得正確類型的標準或使用者定義轉換。 轉換的應用會受限於下列規則：

- 若轉換包含多個使用者定義的轉換，則不考慮其序列。

- 若轉換可以藉由移除中繼轉換而縮短，則不考慮其序列。

轉換產生的序列 (如果有的話) 稱為「最相符序列」(Best Matching Sequence)。 有數種方式可使用標準轉換將類型的物件轉換 **`int`** 為類型 **`unsigned long`** （如[標準轉換](../cpp/standard-conversions.md)中所述）：

- 從轉換 **`int`** 成 **`long`** ，然後從轉換成 **`long`** **`unsigned long`** 。

- 從轉換 **`int`** 成 **`unsigned long`** 。

第一個序列雖然達到所需的目標，但並不是最符合的順序，但仍有較短的順序。

下表將顯示稱為一般轉換 (Trivial Conversion) 的轉換群組，這類轉換對於判斷最符合序列的效果有限。 有關一般轉換影響序列選擇的執行個體，將在下表後面的清單中討論。

### <a name="trivial-conversions"></a>一般轉換

|轉換來源類型|轉換目標類型|
|-----------------------|---------------------|
|*類型-名稱*|*類型-名稱***&**|
|*類型-名稱***&**|*類型-名稱*|
|*類型名稱* **[]**|*類型-名稱*__\*__|
|*類型名稱* **（** *引數清單* **）**|**（** __\*__ *類型名稱* **）（** *引數清單* **）**|
|*類型-名稱*|**`const`***類型-名稱*|
|*類型-名稱*|**`volatile`***類型-名稱*|
|*類型-名稱*__\*__|**`const`***類型-名稱*__\*__|
|*類型-名稱*__\*__|**`volatile`***類型-名稱*__\*__|

轉換嘗試執行的序列如下：

1. 完全相符。 呼叫函式所使用的類型與函式原型中所宣告的類型之間完全相符的項目，必定是最相符項目。 一般轉換的序列會分類為完全相符項目。 不過，未進行任何轉換的序列，會被視為優於轉換的序列：

   - From 指標，指向 **`const`** （ `type` <strong>\*</strong> 至 **`const`** `type` <strong>\*</strong> ）的指標。

   - From 指標，指向 **`volatile`** （ `type` <strong>\*</strong> 至 **`volatile`** `type` <strong>\*</strong> ）的指標。

   - 從參考，到的參考 **`const`** （ `type` **&** 至 **`const`** `type` **&** ）。

   - 從參考，到的參考 **`volatile`** （ `type` **&** 至 **`volatile`** `type` **&** ）。

1. 使用提升的相符項目。 任何未分類為完全相符的序列，只包含整數提升、從轉換 **`float`** 為 **`double`** ，以及一般轉換會使用升級分類為相符項。 雖然不如任何完全相符項目一般合適，但是使用提升的相符項目與使用標準轉換的相符項目相比之下仍較為理想。

1. 使用標準轉換的相符項目。 未分類為完全相符或使用提升的相符項目，而且只包含標準轉換和一般轉換的任何序列，都會分類為使用標準轉換的相符項目。 這個分類適用下列規則：

   - 從衍生類別的指標轉換為直接或間接基類的指標，最好是轉換成 `void *` 或 `const void *` 。

   - 從指標轉換成衍生類別、轉換成基底類別的指標會產生較佳的相符項目，基底類別也會越接近直接基底類別。 假設類別階層架構如下圖所示。

![慣用轉換的圖表](../cpp/media/vc391t1.gif "慣用轉換的圖表") <br/>
顯示慣用轉換的圖表

從 `D*` 類型轉換成 `C*` 類型，比從 `D*` 類型轉換成 `B*` 類型更理想。 同樣地，從 `D*` 類型轉換成 `B*` 類型，比從 `D*` 類型轉換成 `A*` 類型更理想。

相同的規則適用於參考轉換。 從 `D&` 類型轉換成 `C&` 類型，比從 `D&` 類型轉換成 `B&` 類型更理想，以此類推。

相同的規則適用於指標至成員轉換。 從 `T D::*` 類型轉換成 `T C::*` 類型，比從 `T D::*` 類型轉換成 `T B::*` 類型更理想，以此類推 (其中 `T` 是成員的類型)。

前述規則僅適用於所指的衍生路徑。 以下圖顯示的圖形為例。

![顯示慣用轉換的多個&#45;繼承](../cpp/media/vc391t2.gif "顯示慣用轉換的多個&#45;繼承") <br/>
顯示慣用轉換的多重繼承圖形

從 `C*` 類型轉換成 `B*` 類型，比從 `C*` 類型轉換成 `A*` 類型更理想。 這是因為它們位於相同路徑上，且 `B*` 較接近。 不過，從類型轉換成類型 `C*` `D*` 不是比較理想的轉換成類型 `A*` ; 因為轉換會遵循不同的路徑，所以沒有任何喜好設定。

1. 使用使用者定義轉換的相符項目 此順序無法分類為完全相符、使用促銷的相符項，或使用標準轉換的相符項。 序列必須只包含使用者定義的轉換、標準轉換或一般轉換，才能分類為透過使用者定義轉換的相符項目。 透過使用者定義轉換的相符項目通常會比使用省略符號的相符項目更理想，但仍不如使用標準轉換的相符項目理想。

1. 使用省略符號的相符項目。 符合宣告中省略符號的任何序列都會分類為使用省略符號的相符項目。 這會被視為最弱的相符項。

如果沒有內建的提升或轉換存在，則會套用使用者定義的轉換。 這些轉換會依據所比對的引數類型為基礎選取。 請考慮下列程式碼：

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

類別的可用使用者定義轉換 `UDC` 是來自類型 **`int`** 和類型 **`long`** 。 因此，編譯器會考慮所要比對之物件的類型轉換：`UDC`。 轉換成 **`int`** exists，而且已選取。

在比對引數的過程中，標準轉換可以同時套用至引數和使用者定義轉換的結果。 因此，下列程式碼可執行：

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

在上述範例中，會叫用使用者定義的轉換（ **operator long**）以轉換 `udc` 成類型 **`long`** 。 如果未定義任何使用者定義的類型轉換 **`long`** ，則轉換會如下所示： `UDC` **`int`** 使用使用者定義的轉換，將類型轉換成類型。 然後，從類型到類型的標準轉換 **`int`** **`long`** 會套用以符合宣告中的引數。

如果需要任何使用者定義的轉換以符合引數，則在評估最符合的項時，不會使用標準轉換。 即使有多個候選函數需要使用者定義的轉換，函式也會視為相等。 例如：

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

這兩個版本都 `Func` 需要使用者定義的轉換，才能將類型轉換成 **`int`** 類別類型引數。 可能的轉換包括：

- 從類型轉換 **`int`** 成類型 `UDC1` （使用者定義的轉換）。

- 從類型轉換成 **`int`** 類型， **`long`** 然後轉換成類型 `UDC2` （兩個步驟的轉換）。

雖然第二個需要標準轉換和使用者定義的轉換，但這兩個轉換仍會視為相等。

> [!NOTE]
> 使用者定義轉換會視為以建構方式轉換或以初始化方式轉換 (轉換函式)。 在考慮最符合項目時，這兩種方法會視為相等。

## <a name="argument-matching-and-the-this-pointer"></a>引數比對和 this 指標

類別成員函式的處理方式不同，取決於它們是否宣告為 **`static`** 。 由於非靜態函式具有提供指標的隱含引數 **`this`** ，因此非靜態函式會被視為具有一個以上的引數，而不是靜態函式，否則會宣告為相同。

這些非靜態成員函式要求隱含的 **`this`** 指標必須符合呼叫函式所使用的物件類型，或者，如果是多載運算子，則會要求第一個引數必須符合套用運算子的物件。 （如需多載運算子的詳細資訊，請參閱多載[運算子](../cpp/operator-overloading.md)）。

不同于多載函式中的其他引數，不會引進任何暫存物件，而且在嘗試比對指標引數時，不會嘗試轉換 **`this`** 。

當 `->` 成員選取運算子用來存取類別的成員函式時 `class_name` ， **`this`** 指標引數的類型為 `class_name * const` 。 如果成員宣告為 **`const`** 或 **`volatile`** ，則類型 `const class_name * const` 分別為和 `volatile class_name * const` 。

`.` 成員選取運算子的工作方式完全相同，但有一點除外，就是其物件名稱前方會放置隱含的 `&` (傳址) 運算子。 下列範例顯示如何執行這項工作：

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

`->*` 和 `.*` (成員的指標) 運算子的左運算元處理方式，與具有相符引數的 `.` 和 `->` (成員選取) 運算子相同。

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>成員函式的 Ref 限定詞

Ref 限定詞可以讓成員函式根據所指向的物件 **`this`** 是 rvalue 或左值來多載。  這項功能可在您選擇不提供資料指標存取的情況下，用來避免不必要的複製作業。 例如，假設 class `C` 會初始化其函式中的某些資料，並在成員函式中傳回該資料的複本 `get_data()` 。 如果類型的物件是即將終結的 `C` 右值，則編譯器會選擇 `get_data() &&` 多載，這會移動資料而不復制它。

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>多載的限制

有幾項限制負責管理一組可接受的多載函式：

- 一組多載函式中的任兩個函式必須具有不同的引數清單。

- 單獨依據傳回類型來判斷，具有相同類型引數清單的多載函式為錯誤。

     **Microsoft 特定的**

您可以根據傳回型別來多載**operator new** ，具體而言，是以指定的記憶體模型修飾詞為基礎。

**結束 Microsoft 專有**

- 成員函式不能只多載一個為靜態，而另一個非靜態。

- **`typedef`** 宣告不會定義新的類型;它們會為現有的類型引進同義字。 它們不會影響多載機制。 請考慮下列程式碼：

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   上述兩個函式擁有相同的引數清單。 `PSTR`是類型的同義字 `char *` 。 在成員範圍內，這個程式碼會產生錯誤。

- 列舉類型是不同的類型，可以用來區別多載函式。

- 型別「陣列」和「指標」會視為相同，用於區別多載函式，但僅適用于單獨維度陣列。 這就是為什麼這些多載函式發生衝突，並產生錯誤訊息：

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   對於多維度陣列而言，第二個和後續所有維度都會視為類型的一部分。 因此，它們會是用來區別多載函式：

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>多載、覆寫和隱藏

同一個範圍中任何兩個相同名稱的函式宣告可以參考同一個函式，也可以參考兩個多載的個別函式。 如果宣告的引數清單包含相同類型的引數 (如先前章節所述)，函式宣告會參考相同的函式。 否則，它們會參考使用多載選取的兩個不同函式。

嚴格觀察到類別範圍;因此，在基類中宣告的函式與衍生類別中所宣告的函式不在同一個範圍內。 如果衍生類別中的函式是使用與基類中的虛擬函式相同的名稱來宣告，衍生類別函式會*覆寫*基類函數。 如需詳細資訊，請參閱[虛擬](../cpp/virtual-functions.md)函式。

如果基類函式未宣告為 ' virtual '，則衍生類別函式會被視為*隱藏*它。 覆寫和隱藏都與多載不同。

嚴格觀察到區塊範圍;因此，在檔案範圍中宣告的函式與在本機宣告的函式不在相同的範圍中。 如果本機宣告的函式與在檔案範圍中宣告的函式相同名稱，本機宣告的函式會隱藏檔案範圍涵式，而不會引發多載。 例如：

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

上述程式碼會顯示函式 `func` 的兩個定義。 採用類型引數的定義在 `char *` 本機， `main` 因為 **`extern`** 語句是。 因此，會隱藏採用類型之引數的定義 **`int`** ，而對的第一個呼叫 `func` 會發生錯誤。

對於多載成員函式，可以將不同的存取權限授與不同版本的函式。 這些函式仍在封入類別的範圍內，因此是多載函式。 請考慮下列程式碼，其中的成員函式 `Deposit` 是多載函式；其中一個是公用版本，另一個則是私用版本。

這個範例的目的在於提供 `Account` 類別，在此類別中需要有正確的密碼才能執行儲放。 其做法是使用多載。

對的呼叫 `Deposit` 會 `Account::Deposit` 呼叫私用成員函式。 這個呼叫是正確的 `Account::Deposit` ，因為是成員函式，而且可以存取類別的私用成員。

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>另請參閱

[函數（c + +）](../cpp/functions-cpp.md)
