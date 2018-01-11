---
title: "使用者定義型別轉換 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: explicit_cpp
dev_langs: C++
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 561730527a215d5314f7239affc764d9f5925f67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-type-conversions-c"></a>使用者定義類型轉換 (C++)
A*轉換*產生的值從某種類型的不同類型的新值。 *標準轉換*其內建類型，而且您可以建立 c + + 語言與支援內建*使用者定義轉換*執行至、 或使用者定義型別之間的轉換。  
  
 標準轉換可以執行內建類型之間的轉換、有繼承關係之類型的指標或參考之間的轉換、轉換成 Void 指標或從 Void 指標轉換，以及轉換成 null 指標。 如需詳細資訊，請參閱[標準轉換](../cpp/standard-conversions.md)。 使用者定義轉換可執行使用者定義類型之間的轉換，或是使用者定義類型與內建類型之間的轉換。 您可以實作以[轉換建構函式](#ConvCTOR)或[轉換函式](#ConvFunc)。  
  
 轉換可以是明確的 (當程式設計人員呼叫一種類型以轉換成另一種類型，例如在轉型或直接初始化作業中) 或隱含的 (當語言或程式呼叫的類型不同於程式設計人員指定的類型時)。  
  
 在下列情況會嘗試隱含轉換：  
  
-   提供給函式的引數沒有與對應參數相同的類型。  
  
-   從函式傳回的值沒有與函式傳回類型相同的類型。  
  
-   初始設定式運算式沒有與其初始化之物件相同的類型。  
  
-   用來控制條件陳述式、迴圈建構或參數的運算式，沒有加以控制所需的結果類型。  
  
-   提供給運算子的運算元沒有與對應運算元參數相同的類型。 若為內建運算子，這兩種運算元必須具有相同的類型，並轉換成可代表兩者的共同類型。 如需詳細資訊，請參閱[標準轉換](standard-conversions.md)。 若為使用者定義運算子，每個運算元都必須要有與對應運算元參數相同的類型。  
  
 當一個標準轉換無法完成隱含轉換時，編譯器可以使用使用者定義轉換，後面接選擇的其他標準轉換，以完成轉換。  
  
 當轉換網站上有兩個以上執行相同轉換的使用者定義轉換時，則將該轉換視為模稜兩可。 這種模稜兩可的情況是種錯誤，因為編譯器無法判斷應選擇哪個可用的轉換。 不過，這並不只是定義多種方式來執行相同轉換的錯誤，因為在原始程式碼不同位置的可用轉換集可能會不同，例如，取決於原始程式檔內含哪些標頭檔。 只要轉換網站上只有一個可用的轉換，就不會模稜兩可。 發生模稜兩可轉換的方式有好幾種，最常見的方式如下：  
  
-   多重繼承。 在多個基底類別中定義該轉換。 
  
-   模稜兩可函式呼叫。 轉換定義為目標類型的轉換建構函式，以及來源類型的轉換函式。 如需詳細資訊，請參閱[轉換函式](#ConvFunc)。  
  
 只要更完整地限定相關類型的名稱，或是執行明確的轉型來釐清您的意圖，通常就能解決模稜兩可的問題。  
  
 轉換建構函式和轉換函式都遵循成員存取控制規則，但是只有在能夠判定明確轉換時，才會考慮轉換的存取範圍。 這表示，即使競爭轉換的存取層級會防止轉換被使用，轉換還是可能會模稜兩可。 如需成員存取範圍的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。  
  
## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>明確的關鍵字以及隱含轉換的問題  
 依預設，當您建立使用者定義的轉換時，編譯器可以用它來執行隱含的轉換。 有時候您就是想這麼做，但有時候在進行隱含轉換時，用來指引編譯器的簡單規則會引導它接受您不想要讓它接受的程式碼。  
  
 有一個隱含轉換會導致問題的知名範例，就是轉換為 `bool`。 有許多原因會讓您想要建立可在布林內容中使用的類別類型 (例如，用來控制 `if` 陳述式或迴圈)，但是之後當編譯器執行使用者定義類型轉換成內建類型的作業時，就會允許編譯器套用其他標準轉換。 這個其他標準轉換的目的，是要允許從 `short` 提升至 `int` 之類的事情，但這也為較不明確的轉換開啟一道門，例如從 `bool` 轉換至 `int`，這會允許您的類別類型用在您絕不想要的整數內容中。 此特定問題就所謂*安全 Bool 問題*。 這種問題就可以用 `explicit` 關鍵字來幫忙。  
  
 `explicit` 關鍵字會告訴編譯器，不能使用指定的轉換來執行隱含轉換。 在引進 `explicit` 關鍵字之前，如果您想要享有隱含轉換的語法便利性，就必須接受隱含轉換有時候會產生非預期的後果，否則就必須使用較不方便的命名轉換函式做為解決方法。 現在，藉由使用 `explicit` 關鍵字，您就可以建立只能用來執行明確轉型或直接初始化的方便轉換，而且不會導致「安全 Bool 問題」之類的問題。  
  
 自 C++98 開始，`explicit` 關鍵字可套用至轉換建構函式，自 C++11 開始，可套用至轉換函式。 下列章節包含如何使用 `explicit` 關鍵字的詳細資訊。  
  
##  <a name="ConvCTOR"></a>轉換建構函式  
 轉換建構函式可定義從使用者定義或內建類型轉換成使用者定義類型的作業。 下列範例示範從內建類型 `double` 轉換成使用者定義類型 `Money` 的轉換建構函式。  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance.amount << std::endl;  
}  
  
int main(int argc, char* argv[])  
{  
    Money payable{ 79.99 };  
  
    display_balance(payable);  
    display_balance(49.95);  
    display_balance(9.99f);  
  
    return 0;  
}  
```  
  
 請注意，第一次呼叫函式 `display_balance` (採用類型 `Money` 的引數) 時不需要轉換，因為其引數是正確的類型。 不過，在第二個呼叫`display_balance`，需要轉換，因為引數型別`double`值是`49.95`，是不函式所預期的內容。 該函式不能直接使用此值，但是因為有一個從引數類型 `double` 轉換為對應參數類型 `Money` 的轉換作業，所以從引數建構了類型 `Money` 的暫時值，並用來完成函式呼叫。 在第三個呼叫`display_balance`，請注意，引數不是`double`，而是`float`值是`9.99`— 尚未函式呼叫可以仍然完成，因為編譯器可以執行標準轉換和 — 在此情況下從`float`至`double`— 然後執行使用者定義的轉換，從`double`至`Money`完成必要的轉換。  
  
### <a name="declaring-conversion-constructors"></a>宣告轉換建構函式  
 下列規則適用於宣告轉換建構函式：  
  
-   轉換的目標類型是所建構的使用者定義類型。  
  
-   轉換建構函式通常只會採用一個引數，屬於此來源類型。 不過，如果其他每個參數都有預設值，轉換建構函式就可以指定其他參數。 來源類型仍是第一個參數的類型。  
  
-   轉換建構函式就像所有建構函式一樣，並沒有指定傳回類型。 在宣告中指定傳回類型是一種錯誤。  
  
-   轉換建構函式可以是明確的。  
  
### <a name="explicit-conversion-constructors"></a>明確轉換建構函式  
 如果將轉換建構函式宣告為 `explicit`，就只能用來執行物件的直接初始化，或執行明確的轉型。 如此可以防止接受類別類型引數的函式，不會也隱含地接受轉換建構函式來源類型的引數，並防止類別類型從來源類型的值以複製的方式初始化。 下列範例示範如何定義明確的轉換建構函式，並示範它對何種程式碼產生格式正確的影響。  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    explicit Money(double _amount) : amount{ _amount } {};  
  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance.amount << std::endl;  
}  
  
int main(int argc, char* argv[])  
{  
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.  
  
    display_balance(payable);      // Legal: no conversion required  
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.  
    display_balance((Money)9.99f); // Legal: explicit cast to Money  
  
    return 0;  
}  
```  
  
 在此範例中，請注意，您仍可使用明確的轉換建構函式來執行 `payable` 的直接初始化。 如果您要以複製方式初始化 `Money payable = 79.99;`，則會是個錯誤。 第一次呼叫 `display_balance` 時並不受影響，因為引數是正確的類型。 第二次呼叫 `display_balance` 時則是個錯誤，因為轉換建構函式不能用來執行隱含轉換。 第三次呼叫 `display_balance` 是合法的，因為是明確地轉型為 `Money`，但請注意，編譯器還是要插入從 `float` 到 `double` 的隱含轉型，以幫助完成轉型。  
  
 雖然允許隱含轉換的便利性很吸引人，但是這麼做會造成難以找出的 Bug。 經驗告訴我們，除非您確定想要讓特定的轉換隱含發生，否則最好是讓所有轉換建構函式都很明確。  
  
##  <a name="ConvFunc"></a>轉換函式  
 轉換函式可定義從使用者定義類型到其他類型的轉換作業。 這些函式有時候是指「轉型運算子」，因為當值轉型為不同類型時，會將其連同轉換建構函式一起呼叫。 下列範例示範從使用者定義類型 `Money` 轉換為內建類型 `double` 的轉換函數：  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    operator double() const { return amount; }  
private:  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << balance << std::endl;  
}  
  
```  
  
 請注意，成員變數 `amount` 設為私用，而引進類型 `double` 的公用轉換函式只是為了傳回 `amount` 的值。 在函式 `display_balance` 中，使用資料流插入運算子 `balance` 將 `<<` 的值以資料流傳送至標準輸出時，會發生隱含轉換。 由於並沒有為使用者定義類型 `Money` 定義任何資料流插入運算子，但是內建類型 `double` 卻有一個資料流插入運算子，因此編譯器可以使用從 `Money` 到 `double` 的轉換函式，以滿足資料流插入運算子。  
  
 衍生類別會繼承轉換函式。 當衍生類別中的轉換函式轉換成完全相同的類型時，只會覆寫繼承的轉換函式。 例如，雖然標準轉換會定義 `operator int` 與 `operator short` 之間的轉換關聯性，但是衍生類別 `int` 的使用者定義轉換函式不會覆寫 (甚至影響) 基底類別 `short` 的使用者定義轉換函式。  
  
### <a name="declaring-conversion-functions"></a>宣告轉換函式  
 下列規則適用於宣告轉換函式：  
  
-   必須先宣告轉換的目標類型，才能宣告轉換函式。 不能在轉換函式的宣告中宣告類別、結構、列舉和 typedef。  
  
    ```  
    operator struct String { char string_storage; }() // illegal  
    ```  
  
-   轉換函式不接受引數。 在宣告中指定任何參數都是錯誤。  
  
-   轉換函式具有以轉換函式名稱 (也是轉換的目標類型名稱) 指定的傳回類型。 在宣告中指定傳回類型是一種錯誤。  
  
-   轉換函式可以是虛擬的。  
  
-   轉換函式可以是明確的。  
  
### <a name="explicit-conversion-functions"></a>明確的轉換函式  
 當轉換函式宣告為明確時，就只能用來執行明確轉型。 如此可以防止接受轉換函式目標類型引數的函式，不會也隱含地接受類別類型的引數，並防止目標類型的執行個體從類別類型的值以複製方式初始化。 下列範例示範如何定義明確的轉換函式，並示範它對何種程式碼產生格式正確的影響。  
  
```  
#include <iostream>  
  
class Money  
{  
public:  
    Money() : amount{ 0.0 } {};  
    Money(double _amount) : amount{ _amount } {};  
  
    explicit operator double() const { return amount; }  
private:  
    double amount;  
};  
  
void display_balance(const Money balance)  
{  
    std::cout << "The balance is: " << (double)balance << std::endl;  
}  
  
```  
  
 這裡的轉換函式 `operator double` 已設為明確，並已在函式 `double` 中引進為類型 `display_balance` 的明確轉型，以執行轉換。 如果省略此轉型，編譯器會找不到適合類型 `<<` 的資料流插入運算子 `Money`，並且會發生錯誤。  
  
