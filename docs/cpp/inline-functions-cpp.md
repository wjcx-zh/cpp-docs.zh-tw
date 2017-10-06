---
title: "內嵌函式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ef57fae985184595ed32dc78b2280e76ba078e56
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="inline-functions-c"></a>內嵌函式 (C++)
在類別宣告的主體中定義的函式是內嵌函式。  
  
## <a name="example"></a>範例  
 在下列類別宣告中，`Account` 建構函式是內嵌函式。 成員函式`GetBalance`， `Deposit`，和`Withdraw`未指定為**內嵌**但可以實作為內嵌函式。  
  
```  
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
>  在類別宣告中，函式已宣告為不具有**內嵌**關鍵字。 **內嵌**關鍵字可以在類別宣告中指定，則結果會相同。  
  
 指定的內嵌成員函式在每個編譯單位中必須以相同方式宣告。 這個條件約束會造成內嵌函式的行為如同具現化函式。 此外，必須只有一個內嵌函式的定義。  
  
 類別成員函式會預設為外部連結，除非該函式的定義包含**內嵌**規範。 先前的範例顯示，這些函式需要不以明確宣告**內嵌**規範，則使用**內嵌**函式中定義會使它變成內嵌函式。 不過，您不能重新宣告函式做**內嵌**之後呼叫此函式。  
  
## <a name="inline-inline-and-forceinline"></a>Inline、 __inline、 和\__forceinline  
 `inline` 和 `__inline` 規範指示編譯器插入一份函式主體到函式被呼叫的每個地方。  
  
 只有在編譯器的成本/效益分析顯示為有利時，插入 (稱為內嵌展開或內嵌) 動作才會發生。 內嵌展開用較大的程式碼大小來換取函式呼叫負荷減輕。  
  
 `__forceinline` 關鍵字覆寫成本/效益分析，並改為依靠程式設計人員的判斷。 使用 `__forceinline` 時請小心。 隨意亂用 `__forceinline` 可能會導致只邊際效能提升的較大程式碼，在某些情況下，甚至效能損失 (例如，因為較大型可執行檔的分頁增加)。  
  
 使用內嵌函式可以讓程式更快速，因為它們不需要與函式呼叫相關聯的負荷。 內嵌展開的函式必須遵從不適用於一般函式的程式碼最佳化。  
  
 編譯器會將內嵌展開選項和關鍵字視為建議， 並不保證函式一定會內嵌。 您無法強制編譯器內嵌特定的函式，即使是使用 `__forceinline` 關鍵字。 編譯時**/clr**，編譯器不會內嵌函式是否有安全性屬性套用至函式。  
  
 **內嵌**關鍵字是只能在 c + + 中使用。 `__inline` 與 `__forceinline` 關鍵字可在 C 和 C++ 中使用。 為了與舊版中，相容**_inline**同義`__inline`。  
  
 **內嵌**關鍵字會指示編譯器內嵌展開為慣用。 不過，編譯器可能會建立函式的個別執行個體 (具現化) 和建立標準呼叫連結，而不是將程式碼內嵌插入。 在兩種情況下，可能發生這種情況：  
  
-   遞迴函式  
  
-   透過在轉譯單位其他地方的指標所參考的函式。  
  
 這些原因可能干擾內嵌 （inline)*為其他*，全權決定編譯器; 您不應依賴**內嵌**規範造成函式內嵌。  
  
 如同一般函式，內嵌函式引數評估沒有已定義的順序。 實際上，它可能不同於在使用一般函式呼叫通訊協定傳遞時評估引數的順序。  
  
 [須遵循 /Ob](../build/reference/ob-inline-function-expansion.md)編譯器最佳化選項可協助判斷內嵌函式展開是否確實發生。  
  
 [/LTCG](../build/reference/ltcg-link-time-code-generation.md)執行跨模組內嵌，不論是否已在原始程式碼中要求。  
  
### <a name="example-1"></a>範例 1  
  
```  
// inline_keyword1.cpp  
// compile with: /c  
inline int max( int a , int b ) {  
   if( a > b )   
      return a;  
   return b;  
}  
```  
  
 類別成員函式即可宣告為內嵌使用**內嵌**關鍵字或藉由放置在類別定義中的函式定義。  
  
### <a name="example-2"></a>範例 2  
  
```  
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
  
### <a name="microsoft-specific"></a>Microsoft 特定的  
 `__inline`關鍵字相當於**內嵌**。  
  
 儘管使用 `__forceinline`，編譯器仍無法在所有情況下內嵌程式碼。 在下列情況下，編譯器無法內嵌函式：  
  
-   函式或它的呼叫端使用 /Ob0 編譯 (偵錯組建的預設選項)。  
  
-   函式和呼叫端使用不同的例外狀況處理 (一個使用 C++ 例外狀況處理，另一個使用結構化例外狀況處理)。  
  
-   函式具有變數引數清單。  
  
-   函式使用內嵌組譯碼，除非使用 /Og、/Ox、/O1 或 /O2 編譯。  
  
-   此函式是遞迴的未伴隨**#pragma inline_recursion （on)**。 伴隨 pragma，遞迴函式內嵌至預設為 16 個呼叫的深度。 若要減少內嵌深度，使用[inline_depth](../preprocessor/inline-depth.md) pragma。  
  
-   函式是虛擬的，也是以虛擬方式呼叫。 對虛擬函式的直接呼叫可以內嵌。  
  
-   程式使用函式的位址，而且此呼叫是透過函式指標進行的。 其位址已取用之函式的直接呼叫可以內嵌。  
  
-   此函式也標記著[naked](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md)修飾詞。  
  
 如果編譯器無法內嵌宣告的函式`__forceinline`，它會產生層級 1 警告，除非：
  
-   使用 /Od 或 /Ob0 編譯函式。 無法內嵌預期在這些情況下。     
  
-   函式中包含的程式庫或另一個轉譯單位中，在外部，定義，或目標虛擬呼叫或間接呼叫目標。 編譯器無法辨識非內嵌找不到目前的轉譯單位中的程式碼。  
  
 遞迴函式可以內嵌替代到所指定的深度[inline_depth](../preprocessor/inline-depth.md) pragma，最多 16 個呼叫。 該深度之後，遞迴函式呼叫視為函式執行個體的呼叫。  由內嵌啟發學習法所檢查之遞迴函式的深度不能超過 16。 [Inline_recursion](../preprocessor/inline-recursion.md) pragma 控制目前底下展開的函式的內嵌展開。 請參閱[內嵌函式展開](../build/reference/ob-inline-function-expansion.md)(/ Ob) 編譯器選項，如需相關資訊。  
  
**END Microsoft 特定的**  
 如需有關使用**內嵌**規範，請參閱：  
  
-   [內嵌類別成員函式](../cpp/inline-functions-cpp.md)  
  
-   [使用 dllexport 和 dllimport 定義內嵌 C++ 函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
## <a name="when-to-use-inline-functions"></a>何時使用內嵌函式  
 內嵌函式用於小型功能時最為理想，例如存取私用資料成員。 這些一行或兩行的「存取子」函式主要用途是傳回有關物件的狀態資訊，而較短的函式容易受到函式呼叫的額外負荷影響。 比例上來說，較長的函式在呼叫/傳回序列中所花的時間較短，因此內嵌時的優勢較少。  
  
 A`Point`可以定義類別，如下所示：  
  
```  
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
  
 假設座標管理是用戶端中的這種類別，指定兩個存取子函式相當常見的作業 (`x`和`y`在上述範例中) 做為**內嵌**通常儲存上的額外負荷：  
  
-   函式呼叫 (包括參數傳遞以及將物件的位址放置在堆疊上)  
  
-   保留呼叫端的堆疊框架  
  
-   新堆疊框架設定  
  
-   傳回值通訊  
  
-   舊堆疊框架還原  
  
-   Return  
  
## <a name="inline-functions-vs-macros"></a>內嵌函式和巨集比較  
 雖然內嵌函式類似巨集 (因為函式程式碼會在編譯時期於呼叫的位置展開)，但是內嵌函式是由編譯器剖析，而巨集則是由前置處理器展開。 因此，兩者有數項重要的差異：  
  
-   內嵌函式會遵循一般功能強制執行的所有類型安全通訊協定。  
  
-   內嵌函式使用指定的相同語法與其他函式不同之處在於它們包含**內嵌**函式宣告中的關鍵字。  
  
-   做為引數傳遞至內嵌函式的運算式會評估一次。 在某些情況下，做為引數傳遞至巨集的運算式可以多次評估。  
  
 下列範例示範將小寫字母轉換為大寫的巨集：  
  
```  
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
  
 運算式的目的`toupper(getc(stdin))`是一個字元應該讀取主控台裝置 (`stdin`)，而如果有必要，轉換為大寫。  
  
 由於實作巨集的緣故，`getc` 會執行一次，判斷字元是否大於或等於 "a"，並且再執行一次，判斷字元是否小於或等於 "z"。 如果字元在該範圍內，`getc` 會再次執行，將字元轉換成大寫。 這表示，程式會等待兩個或三個字元，不過，理想的狀況是只等待一個字元。  
  
 內嵌函式可補救前述問題：  
  
```  
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
 [noinline](../cpp/noinline.md)   
 [auto_inline](../preprocessor/auto-inline.md)
