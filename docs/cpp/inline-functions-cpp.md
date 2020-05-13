---
title: 內嵌函式 (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: 703c04873a733d068da025b595909ecc681ff147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374092"
---
# <a name="inline-functions-c"></a>內嵌函式 (C++)

在類別宣告的主體中定義的函式是內嵌函式。

## <a name="example"></a>範例

在下列類別宣告中，`Account` 建構函式是內嵌函式。 成員函數`GetBalance``Deposit`、`Withdraw`未 指定為**內聯**,但可以作為內聯函數實現。

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
> 在類聲明中,函數聲明時沒有**內聯**關鍵字。 內**聯**關鍵字可以在類聲明中指定;因此,可以在類聲明中指定內聯關鍵字。結果相同。

指定的內嵌成員函式在每個編譯單位中必須以相同方式宣告。 這個條件約束會造成內嵌函式的行為如同具現化函式。 此外，必須只有一個內嵌函式的定義。

類成員函數預設為外部連結,除非該函數的定義包含**內聯**指定器。 前面的示例表明,這些函數不需要使用**內聯**指定器顯式聲明;在函數定義中使用**內聯**會導致它是內聯函數。 但是,在調用該函數后將函數重新聲明為**內聯**是非法的。

## <a name="inline-__inline-and-__forceinline"></a>內聯、__inline和\__forceinline

**內聯**和 **__inline**指定器指示編譯器將函數正文的副本插入到呼叫函數的每個位置。

只有在編譯器的成本/效益分析顯示為有利時，插入 (稱為內嵌展開或內嵌) 動作才會發生。 內嵌展開用較大的程式碼大小來換取函式呼叫負荷減輕。

**__forceinline**關鍵字覆蓋成本/收益分析,而是依賴於程式師的判斷。 使用 **__forceinline**時要謹慎。 濫用 **__forceinline**可能導致代碼越大,性能只會略有提升,在某些情況下甚至性能損失(例如,由於較大可執行檔的分頁增加)。

使用內嵌函式可以讓程式更快速，因為它們不需要與函式呼叫相關聯的負荷。 內嵌展開的函式必須遵從不適用於一般函式的程式碼最佳化。

編譯器會將內嵌展開選項和關鍵字視為建議， 並不保證函式一定會內嵌。 即使使用 **__forceinline**關鍵字,也不能強制編譯器內聯特定函數。 使用 **/clr**編譯時,如果對函數應用了安全屬性,編譯器將不會內聯函數。

**內聯**關鍵字僅在C++中可用。 **__inline**和 **__forceinline**關鍵字在 C 和 C++ 中都有。 為了與早期版本相容 **,_inline**和 **_forceinline**是 **__inline**的同義詞,除非指定編譯器選項[\(/Za 禁用語言擴展),](../build/reference/za-ze-disable-language-extensions.md)否則 **__forceinline。**

**內聯**關鍵字告訴編譯器,內聯擴展是首選。 不過，編譯器可能會建立函式的個別執行個體 (具現化) 和建立標準呼叫連結，而不是將程式碼內嵌插入。 在兩種情況下，可能發生這種情況：

- 遞迴函式

- 透過在轉譯單位其他地方的指標所參考的函式。

這些原因可能會干擾編譯器酌情內聯,*可能還有其他原因*;不應依賴**內聯**指定器來導致函數內聯。

如同一般函式，內嵌函式引數評估沒有已定義的順序。 實際上，它可能不同於在使用一般函式呼叫通訊協定傳遞時評估引數的順序。

[/Ob](../build/reference/ob-inline-function-expansion.md)編譯器優化選項有助於確定內聯函數擴展是否實際發生。

[/LTCG](../build/reference/ltcg-link-time-code-generation.md)執行跨模組內聯,無論是否在原始程式碼中請求。

### <a name="example-1"></a>範例 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

可以使用**內聯**關鍵字或將函數定義放在類定義中,內聯聲明類的成員函數。

### <a name="example-2"></a>範例 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Microsoft 特定的**

**__inline**關鍵字等效於**內聯**。

即使 **__forceinline,** 編譯器也不能在所有情況下內聯代碼。 在下列情況下，編譯器無法內嵌函式：

- 函式或它的呼叫端使用 /Ob0 編譯 (偵錯組建的預設選項)。

- 函式和呼叫端使用不同的例外狀況處理 (一個使用 C++ 例外狀況處理，另一個使用結構化例外狀況處理)。

- 函式具有變數引數清單。

- 函式使用內嵌組譯碼，除非使用 /Og、/Ox、/O1 或 /O2 編譯。

- 函數是遞迴的,不附帶 **#pragmainline_recursion(上)**。 伴隨 pragma，遞迴函式內嵌至預設為 16 個呼叫的深度。 要減小內襯深度,請使用[inline_depth](../preprocessor/inline-depth.md)雜注。

- 函式是虛擬的，也是以虛擬方式呼叫。 對虛擬函式的直接呼叫可以內嵌。

- 程式使用函式的位址，而且此呼叫是透過函式指標進行的。 其位址已取用之函式的直接呼叫可以內嵌。

- 該函數還標有[裸](../cpp/naked-cpp.md)[__declspec](../cpp/declspec.md)修飾符。

如果編譯器無法內聯用 **__forceinline**聲明的函數,它將產生級別 1 警告,除非:

- 函數使用 /Od 或 /Ob0 編譯。 在這些情況下,預計不會進行內聯。

- 函數在外部、包含在的庫或其他翻譯單元中定義,或是虛擬呼叫目標或間接呼叫目標。 編譯器無法標識在當前翻譯單元中找不到的非內聯代碼。

遞歸函數可以內聯替換為[inline_depth](../preprocessor/inline-depth.md)雜注指定的深度,最多只能進行 16 個調用。 該深度之後，遞迴函式呼叫視為函式執行個體的呼叫。  由內嵌啟發學習法所檢查之遞迴函式的深度不能超過 16。 [inline_recursion](../preprocessor/inline-recursion.md)雜注控制當前正在擴展的函數的內聯擴展。 有關詳細資訊[,請參閱內聯函數擴展](../build/reference/ob-inline-function-expansion.md)(/Ob) 編譯器選項。

**結束微軟的**

有關使用**內聯**指定器的詳細資訊,請參閱:

- [內嵌類別成員函式](../cpp/inline-functions-cpp.md)

- [使用 dllexport 和 dllimport 定義內聯C++函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>何時使用內嵌函式

內嵌函式用於小型功能時最為理想，例如存取私用資料成員。 這些一行或兩行的「存取子」函式主要用途是傳回有關物件的狀態資訊，而較短的函式容易受到函式呼叫的額外負荷影響。 比例上來說，較長的函式在呼叫/傳回序列中所花的時間較短，因此內嵌時的優勢較少。

類別`Point`的定義如下:

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

假設座標操作是此類類別的客戶端中相對常見的操作,指定兩個存取器函`x`數(`y`在前面的範例中),因為**內聯**通常節省開銷:

- 函式呼叫 (包括參數傳遞以及將物件的位址放置在堆疊上)

- 保留呼叫端的堆疊框架

- 新堆疊框架設定

- 傳回值通訊

- 舊堆疊框架還原

- 傳回

## <a name="inline-functions-vs-macros"></a>內聯函數與宏

雖然內嵌函式類似巨集 (因為函式程式碼會在編譯時期於呼叫的位置展開)，但是內嵌函式是由編譯器剖析，而巨集則是由前置處理器展開。 因此，兩者有數項重要的差異：

- 內嵌函式會遵循一般功能強制執行的所有類型安全通訊協定。

- 內聯函數使用與任何其他函數相同的語法進行指定,只不過它們在函數聲明中包含**內聯**關鍵字。

- 做為引數傳遞至內嵌函式的運算式會評估一次。 在某些情況下，做為引數傳遞至巨集的運算式可以多次評估。

下列範例示範將小寫字母轉換為大寫的巨集：

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

運算式`toupper(getc(stdin))`的意圖是應從控制台設備讀取字元 (),`stdin`如有必要,應轉換為大寫。

由於實作巨集的緣故，`getc` 會執行一次，判斷字元是否大於或等於 "a"，並且再執行一次，判斷字元是否小於或等於 "z"。 如果字元在該範圍內，`getc` 會再次執行，將字元轉換成大寫。 這表示，程式會等待兩個或三個字元，不過，理想的狀況是只等待一個字元。

內嵌函式可補救前述問題：

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>另請參閱

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)
