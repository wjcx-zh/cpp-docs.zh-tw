---
title: "內嵌函式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__forceinline_cpp"
  - "__inline_cpp"
  - "inline_cpp"
  - "__forceinline"
  - "__inline"
  - "inline"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內嵌函式, 類別成員"
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 內嵌函式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在類別宣告的主體中定義的函式是內嵌函式。  
  
## 範例  
 在下列類別宣告中，`Account` 建構函式是內嵌函式。  成員函式 `GetBalance`、`Deposit` 和 `Withdraw` 未指定為 **inline**，但是可以做為內嵌函式實作。  
  
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
>  在類別宣告中，函式不會使用 **inline** 關鍵字宣告。  **inline** 關鍵字可以在類別宣告中指定，其結果相同。  
  
 指定的內嵌成員函式在每個編譯單位中必須以相同方式宣告。  這個條件約束會造成內嵌函式的行為如同具現化函式。  此外，必須只有一個內嵌函式的定義。  
  
 除非類別成員函式的定義包含 **inline** 規範，否則該函式會預設為外部連結。  先前的範例顯示，這些函式不需要使用 **inline** 規範明確宣告，在函式定義中使用 **inline** 會造成該函式變成內嵌函式。  不過，在呼叫函式之後重新將該函式宣告為 **inline** 是不合法的。  
  
## inline、\_\_inline 和 \_\_forceinline  
 `inline` 和 `__inline` 規範指示編譯器插入一份函式主體到函式被呼叫的每個地方。  
  
 只有在編譯器的成本\/效益分析顯示為有利時，插入 \(稱為內嵌展開或內嵌\) 動作才會發生。  內嵌展開用較大的程式碼大小來換取函式呼叫負荷減輕。  
  
 `__forceinline` 關鍵字覆寫成本\/效益分析，並改為依靠程式設計人員的判斷。  使用 `__forceinline` 時請小心。  隨意亂用 `__forceinline` 可能會導致只邊際效能提升的較大程式碼，在某些情況下，甚至效能損失 \(例如，因為較大型可執行檔的分頁增加\)。  
  
 使用內嵌函式可以讓程式更快速，因為它們不需要與函式呼叫相關聯的負荷。  內嵌展開的函式必須遵從不適用於一般函式的程式碼最佳化。  
  
 編譯器會將內嵌展開選項和關鍵字視為建議，  並不保證函式一定會內嵌。  您無法強制編譯器內嵌特定的函式，即使是使用 `__forceinline` 關鍵字。  以 **\/clr** 編譯時，如果有安全性屬性套用至此函式，則編譯器不會內嵌函式。  
  
 **inline** 關鍵字只適用於 C\+\+。  `__inline` 與 `__forceinline` 關鍵字可在 C 和 C\+\+ 中使用。  為了與舊版相容，**\_inline** 是 `__inline` 的同義字。  
  
 **inline** 關鍵字會指示編譯器內嵌展開為慣用。  不過，編譯器可能會建立函式的個別執行個體 \(具現化\) 和建立標準呼叫連結，而不是將程式碼內嵌插入。  在兩種情況下，可能發生這種情況：  
  
-   遞迴函式  
  
-   透過在轉譯單位其他地方的指標所參考的函式。  
  
 這些原因可能干擾內嵌 \(如同其他原因\)，由編譯器全權決定；您不應依賴 **inline** 規範造成函式內嵌。  
  
 如同一般函式，內嵌函式引數評估沒有已定義的順序。  實際上，它可能不同於在使用一般函式呼叫通訊協定傳遞時評估引數的順序。  
  
 [\/Ob](../build/reference/ob-inline-function-expansion.md) 編譯器最佳化選項可協助判斷內嵌函式展開是否確實發生。  
  
 [\/LTCG](../build/reference/ltcg-link-time-code-generation.md) 執行跨模組的內嵌，不論在原始程式碼中有無此要求。  
  
### 範例 1  
  
```  
// inline_keyword1.cpp  
// compile with: /c  
inline int max( int a , int b ) {  
   if( a > b )   
      return a;  
   return b;  
}  
```  
  
 藉由 **inline** 關鍵字的使用或透過將函式定義放置在類別定義中，類別的成員函式可以內嵌宣告。  
  
### 範例 2  
  
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
  
### Microsoft 特定的  
 `__inline` 關鍵字相當於 **inline**。  
  
 儘管使用 `__forceinline`，編譯器仍無法在所有情況下內嵌程式碼。  在下列情況下，編譯器無法內嵌函式：  
  
-   函式或它的呼叫端使用 \/Ob0 編譯 \(偵錯組建的預設選項\)。  
  
-   函式和呼叫端使用不同的例外狀況處理 \(一個使用 C\+\+ 例外狀況處理，另一個使用結構化例外狀況處理\)。  
  
-   函式具有變數引數清單。  
  
-   函式使用內嵌組譯碼，除非使用 \/Og、\/Ox、\/O1 或 \/O2 編譯。  
  
-   函式是遞迴，未伴隨 **\#pragma inline\_recursion\(on\)**。  伴隨 pragma，遞迴函式內嵌至預設為 16 個呼叫的深度。  若要減少內嵌深度，請使用 [inline\_depth](../preprocessor/inline-depth.md) pragma。  
  
-   函式是虛擬的，也是以虛擬方式呼叫。  對虛擬函式的直接呼叫可以內嵌。  
  
-   程式使用函式的位址，而且此呼叫是透過函式指標進行的。  其位址已取用之函式的直接呼叫可以內嵌。  
  
-   函式也標記著 [naked](../cpp/naked-cpp.md) [\_\_declspec](../cpp/declspec.md) 修飾詞。  
  
 如果編譯器無法內嵌以 `__forceinline` 宣告的函式，它會產生層級 1 的警告。  
  
 遞迴函式可以內嵌替代到 [inline\_depth](../preprocessor/inline-depth.md) pragma 所指定的深度，指定的深度最多可達 16 個呼叫。  該深度之後，遞迴函式呼叫視為函式執行個體的呼叫。  由內嵌啟發學習法所檢查之遞迴函式的深度不能超過 16。  [inline\_recursion](../preprocessor/inline-recursion.md) pragma 控制目前擴張中函式的內嵌展開。  如需相關資訊，請參閱[內嵌函式展開](../build/reference/ob-inline-function-expansion.md) \/Ob 編譯器選項。  
  
### END Microsoft 特定的  
 如需有關使用 **inline** 規範的詳細資訊，請參閱：  
  
-   [內嵌類別成員函式](../cpp/inline-functions-cpp.md)  
  
-   [內嵌函式和巨集比較](../misc/inline-functions-versus-macros.md)  
  
-   [何時使用內嵌函式](../misc/when-to-use-inline-functions.md)  
  
-   [使用 dllexport 和 dllimport 定義內嵌 C\+\+ 函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
## 何時使用內嵌函式  
 內嵌函式用於小型功能時最為理想，例如存取私用資料成員。  這些一行或兩行的「存取子」函式主要用途是傳回有關物件的狀態資訊，而較短的函式容易受到函式呼叫的額外負荷影響。  比例上來說，較長的函式在呼叫\/傳回序列中所花的時間較短，因此內嵌時的優勢較少。  
  
 `Point` 類別已在[函式呼叫結果](../misc/function-call-results.md)中引入，可依照下述最佳化：  
  
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
  
 假設座標管理在這種類別的用戶端中是相對常見的作業，那麼將兩個存取子函式 \(前述範例中的 `x` 和 `y`\) 指定為 **inline** 通常可在以下方面省去額外負荷：  
  
-   函式呼叫 \(包括參數傳遞以及將物件的位址放置在堆疊上\)  
  
-   保留呼叫端的堆疊框架  
  
-   新堆疊框架設定  
  
-   傳回值通訊  
  
-   舊堆疊框架還原  
  
-   返回  
  
## 內嵌函式與巨集  
 雖然內嵌函式類似巨集 \(因為函式程式碼會在編譯時期於呼叫的位置展開\)，但是內嵌函式是由編譯器剖析，而巨集則是由前置處理器展開。  因此，兩者有數項重要的差異：  
  
-   內嵌函式會遵循一般功能強制執行的所有類型安全通訊協定。  
  
-   內嵌函式是使用與任何其他函式相同的語法指定，不過它們的函式宣告中會包含 **inline** 關鍵字。  
  
-   做為引數傳遞至內嵌函式的運算式會評估一次。  在某些情況下，做為引數傳遞至巨集的運算式可以多次評估。  
  
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
  
 `toupper(getc(stdin))` 運算式的目的是要從主控台裝置 \(`stdin`\) 讀取字元，並且在必要時，將字元轉換成大寫。  
  
 由於實作巨集的緣故，`getc` 會執行一次，判斷字元是否大於或等於 "a"，並且再執行一次，判斷字元是否小於或等於 "z"。 如果字元在該範圍內，`getc` 會再次執行，將字元轉換成大寫。  這表示，程式會等待兩個或三個字元，不過，理想的狀況是只等待一個字元。  
  
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
  
  **Sample Input: `a`**   
 **Sample Output: `A`**    
## 請參閱  
 [noinline](../cpp/noinline.md)   
 [auto\_inline](../preprocessor/auto-inline.md)