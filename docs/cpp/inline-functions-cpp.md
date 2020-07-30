---
title: 內嵌函式 (C++)
description: C + + inline 關鍵字可以用來向編譯器建議內嵌函式。
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
ms.openlocfilehash: d2356d7813167f3973ac2748423c6af7f0b5573b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227409"
---
# <a name="inline-functions-c"></a>內嵌函式 (C++)

在類別宣告的主體中定義的函式是內嵌函式。

## <a name="example"></a>範例

在下列類別宣告中，`Account` 建構函式是內嵌函式。 成員函式 `GetBalance` 、 `Deposit` 和 `Withdraw` 並未指定為， **`inline`** 但是可以實作為內嵌函式。

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
> 在類別宣告中，函式是以不含關鍵字的方式宣告 **`inline`** 。 **`inline`** 關鍵字可以在類別宣告中指定，結果會相同。

指定的內嵌成員函式在每個編譯單位中必須以相同方式宣告。 這個條件約束會造成內嵌函式的行為如同具現化函式。 此外，必須只有一個內嵌函式的定義。

除非該函式的定義包含規範，否則類別成員函式預設為外部連結 **`inline`** 。 上述範例顯示您不需要使用規範來明確宣告這些函式 **`inline`** 。 **`inline`** 在函式定義中使用，會使它成為內嵌函數。 不過，不允許在呼叫該函式之後重新宣告函式 **`inline`** 。

## <a name="inline-__inline-and-__forceinline"></a>`inline`、`__inline` 和 `__forceinline`

和規範會指示編譯器將函式 **`inline`** **`__inline`** 主體的複本插入至呼叫函式的每個位置。

只有在編譯器的成本效益分析顯示有意義時，才會發生*插入（稱為**內嵌展開*或內嵌）。 內嵌擴充會以較大的程式碼大小的可能成本，將函式呼叫的額外負荷降到最低。

**`__forceinline`** 關鍵字會覆寫成本效益分析，並改為依賴程式設計人員的判斷。 使用時請小心 **`__forceinline`** 。 的任意使用 **`__forceinline`** 可能會產生較大的程式碼，而且只會提升效能，而在某些情況下，甚至會造成效能損失（例如，較大的可執行檔的分頁增加）。

使用內嵌函式可以讓程式更快速，因為它們不需要與函式呼叫相關聯的負荷。 內嵌展開的函式必須遵從不適用於一般函式的程式碼最佳化。

編譯器會將內嵌展開選項和關鍵字視為建議， 不保證函式將會內嵌。 您不能強制編譯器內嵌特定函式，即使使用關鍵字也一樣 **`__forceinline`** 。 使用進行編譯時 **`/clr`** ，如果函式已套用安全性屬性，則編譯器不會內嵌函式。

**`inline`** 關鍵字僅適用于 c + +。 **`__inline`** 和 **`__forceinline`** 關鍵字都可以在 C 和 c + + 中使用。 為了與舊版相容， **`_inline`** 和 **`_forceinline`** 是的同義字 **`__inline`** ， **`__forceinline`** 除非指定了編譯器選項 [ [ `/Za` \( 停用語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能]）。

**`inline`** 關鍵字會告訴編譯器偏好內嵌展開。 不過，編譯器可能會建立函式的個別執行個體 (具現化) 和建立標準呼叫連結，而不是將程式碼內嵌插入。 有兩種情況可能會發生這種行為：

- 遞迴函式

- 透過在轉譯單位其他地方的指標所參考的函式。

這些原因可能會干擾內嵌，而*不像其他人一樣*，也就是編譯器的判斷。您不應該依賴 **`inline`** 規範來使函式成為內嵌。

如同一般函式，內嵌函數中的引數評估沒有已定義的順序。 事實上，使用一般函式呼叫通訊協定傳遞時，它可能會與引數評估順序不同。

[`/Ob`](../build/reference/ob-inline-function-expansion.md)編譯器優化選項可協助判斷內嵌函式展開是否確實發生。

[`/LTCG`](../build/reference/ltcg-link-time-code-generation.md)跨模組內嵌是否在原始程式碼中要求。

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

類別的成員函式可以使用 **`inline`** 關鍵字或藉由將函式定義放在類別定義內，以內嵌方式宣告。

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

**Microsoft 特定**

**`__inline`** 關鍵字相當於 **`inline`** 。

即使使用 **`__forceinline`** ，編譯器還是無法在所有情況下內嵌程式碼。 編譯器無法在下列情況內嵌函式：

- 函式或其呼叫端是以編譯 **`/Ob0`** （debug 組建的預設選項）。

- 函式和呼叫端使用不同的例外狀況處理 (一個使用 C++ 例外狀況處理，另一個使用結構化例外狀況處理)。

- 函式具有變數引數清單。

- 除非使用、或進行編譯，否則函式會使用內嵌組解碼 **`/Ox`** **`/O1`** **`/O2`** 。

- 函式是遞迴的，而且沒有 **`#pragma inline_recursion(on)`** 設定。 伴隨 pragma，遞迴函式內嵌至預設為 16 個呼叫的深度。 若要減少內嵌深度，請使用 [`inline_depth`](../preprocessor/inline-depth.md) pragma。

- 函式是虛擬的，也是以虛擬方式呼叫。 對虛擬函式的直接呼叫可以內嵌。

- 程式使用函式的位址，而且此呼叫是透過函式指標進行的。 其位址已取用之函式的直接呼叫可以內嵌。

- 函式也會以修飾詞標記 [`naked`](../cpp/naked-cpp.md) [`__declspec`](../cpp/declspec.md) 。

如果編譯器無法內嵌以宣告的函式 **`__forceinline`** ，它會產生層級1警告，但下列情況除外：

- 函數是使用/Od 或/Ob0. 來編譯 在這些情況下，不需要任何內嵌。

- 函式會在外部、內含的程式庫或其他轉譯單位中定義，或是虛擬呼叫目標或間接呼叫目標。 編譯器無法識別在目前轉譯單位中找不到的非內嵌程式碼。

遞迴函式可以用內嵌程式碼取代為 pragma 所指定的深度 [`inline_depth`](../preprocessor/inline-depth.md) ，最多可達16個呼叫。 該深度之後，遞迴函式呼叫視為函式執行個體的呼叫。  內嵌啟發式檢查遞迴函數的深度不能超過16。 [`inline_recursion`](../preprocessor/inline-recursion.md)Pragma 會控制目前在展開下之函式的內嵌展開。 如需相關資訊，請參閱[內嵌函式展開](../build/reference/ob-inline-function-expansion.md)（/Ob）編譯器選項。

**結束 Microsoft 專有**

如需使用規範的詳細資訊 **`inline`** ，請參閱：

- [內嵌類別成員函式](../cpp/inline-functions-cpp.md)

- [使用 dllexport 和 dllimport 定義內嵌 c + + 函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>何時使用內嵌函式

內嵌函式用於小型功能時最為理想，例如存取私用資料成員。 這一或兩行的「存取子」函式的主要目的是傳回物件的相關狀態資訊。 Short 函數對函式呼叫的額外負荷很敏感。 較長的函式在呼叫和傳回序列中會以較少的時間來花費，而不會因內嵌而降低

`Point`類別可以定義如下：

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

假設座標管理在這種類別的用戶端中是相當常見的作業，請指定兩個存取子函式（ `x` 和 `y` 上述範例中的）， **`inline`** 通常會將額外負荷儲存在：

- 函式呼叫 (包括參數傳遞以及將物件的位址放置在堆疊上)

- 保留呼叫端的堆疊框架

- 新的堆疊框架設定

- 傳回值通訊

- 還原舊的堆疊框架

- 傳回

## <a name="inline-functions-vs-macros"></a>內嵌函式與宏的比較

內嵌函式類似于宏，因為函式程式碼會在編譯時期的呼叫點展開。 不過，內嵌函式是由編譯器進行剖析，而宏則是由預處理器展開。 因此，兩者有數項重要的差異：

- 內嵌函式會遵循一般功能強制執行的所有類型安全通訊協定。

- 內嵌函式是使用與任何其他函式相同的語法來指定，不同之處在于它們在 **`inline`** 函式宣告中包含關鍵字。

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

運算式的目的 `toupper(getc(stdin))` 是應該從主控台裝置（）讀取字元， `stdin` 並在必要時轉換成大寫。

由於宏的執行， `getc` 會執行一次，判斷字元是否大於或等於 "a"，以及一次以判斷它是否小於或等於 "z"。 如果字元在該範圍內，`getc` 會再次執行，將字元轉換成大寫。 這表示程式會等候兩個或三個字元，在理想的情況下，它只應等候一個。

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

[`noinline`](../cpp/noinline.md)<br/>
[`auto_inline`](../preprocessor/auto-inline.md)
