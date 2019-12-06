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
ms.openlocfilehash: efaaacc46f63ac1a702ab2110d35fe80727ead1d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857511"
---
# <a name="inline-functions-c"></a>內嵌函式 (C++)

在類別宣告的主體中定義的函式是內嵌函式。

## <a name="example"></a>範例

在下列類別宣告中，`Account` 建構函式是內嵌函式。 `GetBalance`、`Deposit`和 `Withdraw` 的成員函式未指定為**inline** ，但可實作為內嵌函式。

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
>  在類別宣告中，函式是在沒有**內嵌**關鍵字的情況下宣告。 **Inline**關鍵字可以在類別宣告中指定;結果是相同的。

指定的內嵌成員函式在每個編譯單位中必須以相同方式宣告。 這個條件約束會造成內嵌函式的行為如同具現化函式。 此外，必須只有一個內嵌函式的定義。

類別成員函式預設為外部連結，除非該函數的定義包含**內嵌**規範。 上述範例顯示這些函式不需要使用**內嵌**規範明確宣告;在函式定義中使用**內嵌**，會使它成為內嵌函數。 不過，在呼叫該函式之後，將函式重新宣告為**內嵌**是不合法的。

## <a name="inline-__inline-and-__forceinline"></a>內嵌、__inline 和 \__forceinline

**內嵌**和 **__inline**規範會指示編譯器將函式主體的複本插入至呼叫函式的每個位置。

只有在編譯器的成本/效益分析顯示為有利時，插入 (稱為內嵌展開或內嵌) 動作才會發生。 內嵌展開用較大的程式碼大小來換取函式呼叫負荷減輕。

**__Forceinline**關鍵字會覆寫成本/效益分析，並改為依賴程式設計人員的判斷。 使用 **__forceinline**時，請務必小心。 任意使用 **__forceinline**可能會產生較大的程式碼，而且只會提升效能，而在某些情況下，甚至會造成效能損失（例如，較大的可執行檔的分頁增加）。

使用內嵌函式可以讓程式更快速，因為它們不需要與函式呼叫相關聯的負荷。 內嵌展開的函式必須遵從不適用於一般函式的程式碼最佳化。

編譯器會將內嵌展開選項和關鍵字視為建議， 並不保證函式一定會內嵌。 您不能強制編譯器內嵌特定函式，即使使用 **__forceinline**關鍵字也一樣。 以 **/clr**進行編譯時，如果有套用到函式的安全性屬性，編譯器不會內嵌函式。

**Inline**關鍵字僅適用于C++。 **__Inline**和 **__Forceinline**關鍵字在 C 和C++中都有提供。 為了與舊版相容， **_inline**和 **_forceinline**都是 **__inline**的同義字，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則會 **__forceinline** 。

**Inline**關鍵字會告訴編譯器偏好內嵌展開。 不過，編譯器可能會建立函式的個別執行個體 (具現化) 和建立標準呼叫連結，而不是將程式碼內嵌插入。 在兩種情況下，可能發生這種情況：

- 遞迴函式

- 透過在轉譯單位其他地方的指標所參考的函式。

這些原因可能會干擾內嵌，而*不像其他人一樣*，也就是編譯器的判斷。您不應該依賴**內嵌**規範來使函式成為內嵌。

如同一般函式，內嵌函式引數評估沒有已定義的順序。 實際上，它可能不同於在使用一般函式呼叫通訊協定傳遞時評估引數的順序。

[/Ob](../build/reference/ob-inline-function-expansion.md)編譯器優化選項可協助判斷內嵌函式展開是否確實發生。

[/Ltcg](../build/reference/ltcg-link-time-code-generation.md)會執行跨模組內嵌，不論其是否在原始程式碼中要求。

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

您可以使用**inline**關鍵字或將函式定義放在類別定義內，以內嵌方式宣告類別的成員函式。

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

**Microsoft 專屬**

**__Inline**關鍵字相當於**inline**。

即使使用 **__forceinline**，編譯器還是無法在所有情況下內嵌程式碼。 在下列情況下，編譯器無法內嵌函式：

- 函式或它的呼叫端使用 /Ob0 編譯 (偵錯組建的預設選項)。

- 函式和呼叫端使用不同的例外狀況處理 (一個使用 C++ 例外狀況處理，另一個使用結構化例外狀況處理)。

- 函式具有變數引數清單。

- 函式使用內嵌組譯碼，除非使用 /Og、/Ox、/O1 或 /O2 編譯。

- 函式是遞迴的，不會伴隨 **#pragma inline_recursion （on）** 。 伴隨 pragma，遞迴函式內嵌至預設為 16 個呼叫的深度。 若要減少內嵌深度，請使用[inline_depth](../preprocessor/inline-depth.md) pragma。

- 函式是虛擬的，也是以虛擬方式呼叫。 對虛擬函式的直接呼叫可以內嵌。

- 程式使用函式的位址，而且此呼叫是透過函式指標進行的。 其位址已取用之函式的直接呼叫可以內嵌。

- 函數也會以[naked](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md)修飾詞標記。

如果編譯器無法內嵌以 **__forceinline**宣告的函式，它會產生層級1警告，但下列情況除外：

- 函數是使用/Od 或/Ob0. 來編譯 在這些情況下，不需要任何內嵌。

- 函式會在外部、內含的程式庫或其他轉譯單位中定義，或是虛擬呼叫目標或間接呼叫目標。 編譯器無法識別在目前轉譯單位中找不到的非內嵌程式碼。

遞迴函式可以內嵌替代為[inline_depth](../preprocessor/inline-depth.md) pragma 所指定的深度，最多可達16個呼叫。 該深度之後，遞迴函式呼叫視為函式執行個體的呼叫。  由內嵌啟發學習法所檢查之遞迴函式的深度不能超過 16。 [Inline_recursion](../preprocessor/inline-recursion.md) pragma 會控制目前在展開下之函式的內嵌展開。 如需相關資訊，請參閱[內嵌函式展開](../build/reference/ob-inline-function-expansion.md)（/Ob）編譯器選項。

**結束 Microsoft 專屬**

如需使用**內嵌**規範的詳細資訊，請參閱：

- [內嵌類別成員函式](../cpp/inline-functions-cpp.md)

- [使用 dllexport 和 dllimport 定義內嵌 C++ 函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>何時使用內嵌函式

內嵌函式用於小型功能時最為理想，例如存取私用資料成員。 這些一行或兩行的「存取子」函式主要用途是傳回有關物件的狀態資訊，而較短的函式容易受到函式呼叫的額外負荷影響。 比例上來說，較長的函式在呼叫/傳回序列中所花的時間較短，因此內嵌時的優勢較少。

`Point` 類別可以定義如下：

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

假設座標管理在這類類別的用戶端中是相當常見的作業，請指定兩個存取子函式（在上述範例中`x` 和 `y`）為**內嵌**通常會將額外負荷儲存在：

- 函式呼叫 (包括參數傳遞以及將物件的位址放置在堆疊上)

- 保留呼叫端的堆疊框架

- 新堆疊框架設定

- 傳回值通訊

- 舊堆疊框架還原

- Return

## <a name="inline-functions-vs-macros"></a>內嵌函式與宏的比較

雖然內嵌函式類似巨集 (因為函式程式碼會在編譯時期於呼叫的位置展開)，但是內嵌函式是由編譯器剖析，而巨集則是由前置處理器展開。 因此，兩者有數項重要的差異：

- 內嵌函式會遵循一般功能強制執行的所有類型安全通訊協定。

- 內嵌函式是使用與任何其他函式相同的語法所指定，但它們在函式宣告中包含**inline**關鍵字。

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

運算式 `toupper(getc(stdin))` 的目的是應該從主控台裝置（`stdin`）讀取字元，並在必要時轉換成大寫。

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

## <a name="see-also"></a>請參閱

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)