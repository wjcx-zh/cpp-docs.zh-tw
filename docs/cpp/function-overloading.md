---
title: 函式多載
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: a59c0e27a4500cb20ef42e9a55b4eb0004e07f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368914"
---
# <a name="function-overloading"></a>函式多載

C++ 允許在相同範圍內指定多個同名的函式。 這些函數稱為*重載*函數。 重載函數使您能夠根據參數的類型和數量為函數提供不同的語義。

例如,採用參數`print`的`std::string`函數可能執行的任務可能與採用類型**為 double**的函數的任務執行非常不同的任務。 重載可使您不必使用名稱(如`print_string`或`print_double`)。 在編譯時,編譯器根據調用方傳入的參數類型選擇要使用的重載。  如果調用`print(42.0)`,則`void print(double d)`將調用該函數。 如果調用`print("hello world")`,則`void print(std::string)`將調用重載。

您可以重載成員函數和非成員函數。 下表將說明 C++ 使用函式宣告的哪些部分區分在相同範圍內具有相同名稱的函式群組。

### <a name="overloading-considerations"></a>多載考量

|函式宣告項目|是否用於多載？|
|----------------------------------|---------------------------|
|函式傳回類型|否|
|引數數目|是|
|引數類型|是|
|省略符號是否存在|是|
|使用**型態定義**名稱|否|
|未指定的陣列範圍|否|
|**const**或**揮發性**|是,應用於整個函數時|
|[參考限定詞](#ref-qualifiers)|是|

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

默認參數不被視為函數類型的一部分。 因此,它不用於選擇重載函數。 兩個函式的不同之處只有在其預設引數是視為多重定義而不是多載函式。

無法為重載運算符提供預設參數。

## <a name="argument-matching"></a>引數對應

多載函式會在為了找出目前範圍中最符合函式呼叫所提供引數的函式宣告項目時選取。 如果找到適合的函式，就會呼叫該函式。 在此上下文中的「適當」是指:

- 找到完全相符項目。

- 已執行一般轉換。

- 已執行整數提升。

- 有轉換成所需引數類型的標準轉換存在。

- 有轉換成所需引數類型的使用者定義轉換 (轉換運算子或建構函式) 存在。

- 找到省略符號所表示的引數。

編譯器會為每一個引數建立一組候選函式。 候選函式是指函式中該位置的實際引數可以轉換成正式引數的類型。

每個引數都會有一組建置的「最相符函式」，而且選取的函式是所有集合的交集。 如果交集包含多個函式，則多載會變得模稜兩可並產生錯誤。 最後選取的函式對於至少一個引數來說，永遠是比群組中其他每一個函式更理想的相符項目。 如果沒有明確的贏家,函數調用將生成錯誤。

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

|集合 1：第一個引數為 Fraction 類型的候選函式|設定 2:候選函數其第二個參數可以轉換為類型**int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Variant 1|變體**1(int**可以使用標準轉換轉換為**長**)|
|Variant 3||

Set 2 中的函數是存在從實際參數類型到正式參數類型的隱式轉換的函數,在此類函數中,有一個函數,其中將實際參數類型轉換為其正式參數類型的"成本"最小。

這兩個集合的交集為 Variant 1。 模稜兩可函式呼叫的範例如下：

```cpp
F1 = Add( 3, 6 );
```

上述函式呼叫會建立下列集合：

|第一個項目:具有類型**int**的第一個參數的候選函數|設定 2: 具有類型**int**的第二個參數的候選函數|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|變體**2(int**可以使用標準轉換轉換為**長**)|變體**1(int**可以使用標準轉換轉換為**長**)|

由於這兩個集的交集為空,因此編譯器將生成一條錯誤消息。

對於參數匹配,具有*n*默認參數的函數將被視為*n*+1 單獨的函數,每個函數具有不同數量的參數。

省略符號 (...) 做為萬用字元使用，它會比對任何實質引數。 如果不格外小心地設計重載功能集,則可能導致許多模稜兩可的集。

> [!NOTE]
> 在遇到函數調用之前,無法確定重載函數的歧義。 遇到函式呼叫時，會為函式呼叫中的每個引數建置集合，如此就可以判斷是否有明確的多載存在。 這表示，模稜兩可的情況可能會持續存在程式碼中，直到特定函式呼叫撤銷這些情況為止。

## <a name="argument-type-differences"></a>引數類型差異

多載函式會區分採用不同初始設定式的各種引數類型。 因此，做為多載的用途時，特定類型的引數以及該類型的參考都會視為相同。 因為它們會採用相同的初始設定式，所以會將它們視為相同。 例如，`max( double, double )` 與 `max( double &, double & )` 會視為相同。 同時宣告兩個這類函式會產生錯誤。

出於同樣的原因,為重載目的,由**const**或**volatile**修改的類型的函數參數與基類型不一致。

但是,函數重載機制可以區分通過**const**和**可變性**限定的引用和對基類型的引用。 它使以下代碼成為可能:

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

對於重載目的,指向**const**和**易失性**物件的指標也被視為不同於指向基類型的指標。

## <a name="argument-matching-and-conversions"></a>引數比對和轉換

當編譯器嘗試比對實質引數與函式宣告中的引數時，如果找不到完全相符的項目，它可以提供取得正確類型的標準或使用者定義轉換。 轉換的應用會受限於下列規則：

- 若轉換包含多個使用者定義的轉換，則不考慮其序列。

- 若轉換可以藉由移除中繼轉換而縮短，則不考慮其序列。

轉換產生的序列 (如果有的話) 稱為「最相符序列」(Best Matching Sequence)。 有幾種方法可以將**int**類型的物件轉換為使用標準轉換鍵入**未簽署的長數**(在[標準轉換中](../cpp/standard-conversions.md)描述):

- 從**int**轉換為**長**,然後從**長**轉換為**未簽署長**。

- 從**int**轉換為**未簽署的長**。

第一個序列雖然達到了預期目標,但並不是最佳匹配序列 , 存在較短的序列。

下表將顯示稱為一般轉換 (Trivial Conversion) 的轉換群組，這類轉換對於判斷最符合序列的效果有限。 有關一般轉換影響序列選擇的執行個體，將在下表後面的清單中討論。

### <a name="trivial-conversions"></a>一般轉換

|轉換來源類型|轉換目標類型|
|-----------------------|---------------------|
|*類型名稱*|*類型名稱***&**|
|*類型名稱***&**|*類型名稱*|
|*類型名稱* **|**|*類型名稱*__\*__|
|*型態名稱* **(** *參數清單* **)**|**(** __\*__ *類型名稱* **) (***參數清單* **)**|
|*類型名稱*|**Met** *型態名稱*|
|*類型名稱*|**易失性***型態名稱*|
|*類型名稱*__\*__|**Met** *型態名稱*__\*__|
|*類型名稱*__\*__|**易失性***型態名稱*__\*__|

轉換嘗試執行的序列如下：

1. 完全相符。 呼叫函式所使用的類型與函式原型中所宣告的類型之間完全相符的項目，必定是最相符項目。 一般轉換的序列會分類為完全相符項目。 但是,不進行這些轉換的任何序列被認為優於轉換的序列:

   - 從指標到指標到**const** `type` <strong>\*</strong> ( 到**const** `type` <strong>\*</strong>)。

   - 從指標,到指向**易失性**`type`<strong>\*</strong>指標 (到**易失性**`type`<strong>\*</strong>)。

   - 從參考,到參考**const** `type` **&** ( 到**const** `type` **&**)

   - 從引用,到引用**揮發**性`type`**&**( 到**揮發性**`type`**&**)。

1. 使用提升的相符項目。 任何未歸類為完全匹配的序列,僅包含積分提升、從**浮動**轉換到**雙精度**轉換,以及使用促銷將小轉換歸類為匹配。 雖然不如任何完全相符項目一般合適，但是使用提升的相符項目與使用標準轉換的相符項目相比之下仍較為理想。

1. 使用標準轉換的相符項目。 未分類為完全相符或使用提升的相符項目，而且只包含標準轉換和一般轉換的任何序列，都會分類為使用標準轉換的相符項目。 這個分類適用下列規則：

   - 從指標轉換為派生類,轉換為指向直接或間接基類的指標比轉換為`void *`或`const void *`更可取。

   - 從指標轉換成衍生類別、轉換成基底類別的指標會產生較佳的相符項目，基底類別也會越接近直接基底類別。 假設類別階層架構如下圖所示。

![首選轉換圖](../cpp/media/vc391t1.gif "首選轉換圖") <br/>
顯示首選轉化的圖形

從 `D*` 類型轉換成 `C*` 類型，比從 `D*` 類型轉換成 `B*` 類型更理想。 同樣地，從 `D*` 類型轉換成 `B*` 類型，比從 `D*` 類型轉換成 `A*` 類型更理想。

相同的規則適用於參考轉換。 從 `D&` 類型轉換成 `C&` 類型，比從 `D&` 類型轉換成 `B&` 類型更理想，以此類推。

相同的規則適用於指標至成員轉換。 從 `T D::*` 類型轉換成 `T C::*` 類型，比從 `T D::*` 類型轉換成 `T B::*` 類型更理想，以此類推 (其中 `T` 是成員的類型)。

前述規則僅適用於所指的衍生路徑。 以下圖顯示的圖形為例。

![顯示首選轉換的多個&#45;繼承](../cpp/media/vc391t2.gif "顯示首選轉換的多個&#45;繼承") <br/>
顯示首選轉換的多重繼承圖

從 `C*` 類型轉換成 `B*` 類型，比從 `C*` 類型轉換成 `A*` 類型更理想。 這是因為它們位於相同路徑上，且 `B*` 較接近。 但是,從類型`C*`轉換為類型`D*`的轉換不可取,不如轉換為`A*`類型 。沒有首選項,因為轉換遵循不同的路徑。

1. 使用使用者定義轉換的相符項目 此序列不能歸類為完全匹配、使用促銷匹配或使用標準轉換的匹配。 序列必須只包含使用者定義的轉換、標準轉換或一般轉換，才能分類為透過使用者定義轉換的相符項目。 透過使用者定義轉換的相符項目通常會比使用省略符號的相符項目更理想，但仍不如使用標準轉換的相符項目理想。

1. 使用省略符號的相符項目。 符合宣告中省略符號的任何序列都會分類為使用省略符號的相符項目。 這被認為是最弱的比賽。

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

類別`UDC`的使用者定義的轉換來自**類型 int**與類型**長**。 因此，編譯器會考慮所要比對之物件的類型轉換：`UDC`。 存在轉換為**int,** 並選擇了該轉換。

在比對引數的過程中，標準轉換可以同時套用至引數和使用者定義轉換的結果。 因此，下列程式碼可執行：

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

在前面的範例中,使用者定義的轉換(**運算子長**) 被`udc`呼叫 轉換為**類型長**。 如果未定義使用者定義為類型**長**的轉換,則轉換將如下所示:使用使用者定義的轉換將`UDC`Type 轉換為類型**int。** 然後,將應用從**int**到類型**long**的標準轉換來匹配聲明中的參數。

如果需要任何使用者定義的轉換來匹配參數,則在評估最佳匹配項時不使用標準轉換。 即使多個候選函數需要使用者定義的轉換,這些函數也被視為相等。 例如：

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

的`Func`兩個版本都需要使用者定義的轉換才能將**int**類型轉換為類類型參數。 可能的轉換包括：

- 從**int**類型`UDC1`轉換為類型(使用者定義的轉換)。

- 從類型**int**轉換為**長**型態 。然後轉換為類型`UDC2`(兩步轉換)。

即使第二個轉換同時需要標準轉換和使用者定義的轉換,這兩個轉換仍被視為相等。

> [!NOTE]
> 使用者定義轉換會視為以建構方式轉換或以初始化方式轉換 (轉換函式)。 在考慮最符合項目時，這兩種方法會視為相等。

## <a name="argument-matching-and-the-this-pointer"></a>引數比對和 this 指標

類別成員函數的處理方式不同,具體取決於它們是否聲明為**靜態**。 由於非靜態函數具有提供**此**指標的隱式參數,因此非靜態函數被認為比靜態函數多一個參數;否則,它們被聲明相同。

這些非靜態成員函數要求隱含**的此**指標與調用函數的物件類型匹配,或者對於重載運算符,它們要求第一個參數與應用運算符的物件匹配。 (有關重載運算子的詳細資訊,請參閱[重載運算符號](../cpp/operator-overloading.md)。

與重載函數中的其他參數不同,在嘗試匹配**此**指標參數時,不會引入臨時物件,也未嘗試轉換。

當`->`成員選擇運算子用於存取`class_name`類別的成員函數時,**這個**指標參數的類型為`class_name * const`。 如果成員宣告為**const**或**volatile,** 則類型`const class_name * const`分別為`volatile class_name * const`與 。

`.` 成員選取運算子的工作方式完全相同，但有一點除外，就是其物件名稱前方會放置隱含的 `&` (傳址) 運算子。 下列範例顯示如何執行這項工作：

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

`->*` 和 `.*` (成員的指標) 運算子的左運算元處理方式，與具有相符引數的 `.` 和 `->` (成員選取) 運算子相同。

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>成員函數上的參考限定

ref 限定符可以根據**指向此**對像是 rvalue 還是 lvalue 來重載成員函數。  在選擇不提供對數據的指標訪問的情況下,此功能可用於避免不必要的複製操作。 例如,假設類`C`初始化其構造函數中的某些數據,並在成員函`get_data()`數 中返回該數據的副本。 如果類型`C`對象是即將銷毀的 rvalue,則編譯`get_data() &&`器將選擇 重載,該重載行動資料而不是複製資料。

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

## <a name="restrictions-on-overloading"></a>對超載的限制

有幾項限制負責管理一組可接受的多載函式：

- 一組多載函式中的任兩個函式必須具有不同的引數清單。

- 單獨依據傳回類型來判斷，具有相同類型引數清單的多載函式為錯誤。

     **Microsoft 特定的**

可以僅根據返回類型重新重載**運算符**, 具體地說,基於指定的記憶體模型修飾符。

**結束微軟的**

- 成員函數不能僅基於靜態函數,另一個非靜態函數重載。

- **類型定義**聲明不定義新類型;因此,類型定義聲明聲明不定義新類型。它們為現有類型引入同義詞。 它們不會影響重載機制。 請考慮下列程式碼：

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   上述兩個函式擁有相同的引數清單。 `PSTR`是類型`char *`的同義詞。 在成員範圍內，這個程式碼會產生錯誤。

- 列舉類型是不同的類型，可以用來區別多載函式。

- 為了區分重載函數,並且僅對單獨標註的陣列而言,「陣列」和「指標指向」的類型被視為相同。 這就是為什麼這些重載函數發生衝突並產生錯誤消息的原因:

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

## <a name="overloading-overriding-and-hiding"></a>重載、重寫和隱藏

同一個範圍中任何兩個相同名稱的函式宣告可以參考同一個函式，也可以參考兩個多載的個別函式。 如果宣告的引數清單包含相同類型的引數 (如先前章節所述)，函式宣告會參考相同的函式。 否則，它們會參考使用多載選取的兩個不同函式。

嚴格遵守類範圍;因此,在基類中聲明的函數與派生類中聲明的函數的作用域不同。 如果派生類中的函數聲明的名稱與基類中的虛擬函數同名,則派生類函數*將重寫*基類函數。 有關詳細資訊,請參閱[虛擬函數](../cpp/virtual-functions.md)。

如果基類函數未聲明為"虛擬",則派生類函數稱為*隱藏*它。 重寫和隱藏都不同於重載。

嚴格遵守塊範圍;因此,在檔作用域中聲明的函數與本地聲明的函數的作用域不同。 如果本機宣告的函式與在檔案範圍中宣告的函式相同名稱，本機宣告的函式會隱藏檔案範圍涵式，而不會引發多載。 例如：

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

上述程式碼會顯示函式 `func` 的兩個定義。 `main`由於**外部語句**,採用類型`char *`參數的定義是本地的。 因此,採用**int**參數的定義是隱藏的,並且`func`對的第一個調用是錯誤的。

對於多載成員函式，可以將不同的存取權限授與不同版本的函式。 這些函式仍在封入類別的範圍內，因此是多載函式。 請考慮下列程式碼，其中的成員函式 `Deposit` 是多載函式；其中一個是公用版本，另一個則是私用版本。

這個範例的目的在於提供 `Account` 類別，在此類別中需要有正確的密碼才能執行儲放。 它是通過使用重載來完成的。

調用`Deposit``Account::Deposit`中的調用 調用私有成員函數。 此調用是正確的,因為`Account::Deposit`是一個成員函數,並且有權訪問類的私有成員。

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

[函式 (C++)](../cpp/functions-cpp.md)
