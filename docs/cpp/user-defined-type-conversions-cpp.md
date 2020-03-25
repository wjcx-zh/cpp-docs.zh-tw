---
title: 使用者定義類型轉換 (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
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
ms.openlocfilehash: 055b5bd5c82e4f0be449d548de25267eabef47bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187930"
---
# <a name="user-defined-type-conversions-c"></a>使用者定義類型轉換 (C++)

*轉換*會從不同類型的值產生某種類型的新值。 *標準轉換*內建于C++語言中，並支援其內建類型，您可以建立*使用者定義的轉換*，以執行使用者定義類型之間的轉換。

標準轉換可以執行內建類型之間的轉換、有繼承關係之類型的指標或參考之間的轉換、轉換成 Void 指標或從 Void 指標轉換，以及轉換成 null 指標。 如需詳細資訊，請參閱[標準轉換](../cpp/standard-conversions.md)。 使用者定義轉換可執行使用者定義類型之間的轉換，或是使用者定義類型與內建類型之間的轉換。 您可以將它們實作為[轉換](#ConvCTOR)函式，或當做[轉換函數](#ConvFunc)來執行。

轉換可以是明確的 (當程式設計人員呼叫一種類型以轉換成另一種類型，例如在轉型或直接初始化作業中) 或隱含的 (當語言或程式呼叫的類型不同於程式設計人員指定的類型時)。

在下列情況會嘗試隱含轉換：

- 提供給函式的引數沒有與對應參數相同的類型。

- 從函式傳回的值沒有與函式傳回型別相同的類型。

- 初始設定式運算式沒有與其初始化之物件相同的類型。

- 用來控制條件陳述式、迴圈建構或參數的運算式，沒有加以控制所需的結果類型。

- 提供給運算子的運算元沒有與對應運算元參數相同的類型。 若為內建運算子，這兩種運算元必須具有相同的類型，並轉換成可代表兩者的共同類型。 如需詳細資訊，請參閱[標準轉換](standard-conversions.md)。 若為使用者定義運算子，每個運算元都必須要有與對應運算元參數相同的類型。

當一個標準轉換無法完成隱含轉換時，編譯器可以使用使用者定義轉換，後面接選擇的其他標準轉換，以完成轉換。

當轉換網站上有兩個以上執行相同轉換的使用者定義轉換時，則將該轉換視為模稜兩可。 這種模稜兩可的情況是種錯誤，因為編譯器無法判斷應選擇哪個可用的轉換。 不過，這並不只是定義多種方式來執行相同轉換的錯誤，因為在原始程式碼不同位置的可用轉換集可能會不同，例如，取決於原始程式檔內含哪些標頭檔。 只要轉換網站上只有一個可用的轉換，就不會模稜兩可。 發生模稜兩可轉換的方式有好幾種，最常見的方式如下：

- 多重繼承。 在多個基底類別中定義該轉換。

- 模稜兩可函式呼叫。 轉換定義為目標類型的轉換建構函式，以及來源類型的轉換函式。 如需詳細資訊，請參閱[轉換](#ConvFunc)函式。

只要更完整地限定相關類型的名稱，或是執行明確的轉型來釐清您的意圖，通常就能解決模稜兩可的問題。

轉換建構函式和轉換函式都遵循成員存取控制規則，但是只有在能夠判定明確轉換時，才會考慮轉換的存取範圍。 這表示，即使競爭轉換的存取層級會防止轉換被使用，轉換還是可能會模稜兩可。 如需成員存取範圍的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>明確的關鍵字以及隱含轉換的問題

依預設，當您建立使用者定義的轉換時，編譯器可以用它來執行隱含的轉換。 有時候您就是想這麼做，但有時候在進行隱含轉換時，用來指引編譯器的簡單規則會引導它接受您不想要讓它接受的程式碼。

其中一個可能會造成問題之隱含轉換的知名範例，就是轉換為**bool**。 有許多原因會讓您建立可用於布林內容的類別型別（例如，它可以用來控制**if**語句或迴圈），但是當編譯器對內建型別執行使用者定義的轉換時，編譯器可以在之後套用其他標準轉換。 這項額外標準轉換的目的是要允許從**short**升級為**int**的專案，但它也會針對較不明顯的轉換開啟門，例如從**bool**到**int**，這可讓您的類別類型在您從未預期的整數內容中使用。 這個特定的問題就是所謂的*安全 Bool 問題*。 這種問題是**明確**關鍵字可以提供協助的地方。

**Explicit**關鍵字會告訴編譯器，指定的轉換無法用來執行隱含轉換。 如果您想要在引進**explicit**關鍵字之前隱含轉換的語法便利性，您必須接受隱含轉換有時候會建立的非預期結果，或使用較不方便的命名轉換函數做為因應措施。 現在，藉由使用**explicit**關鍵字，您可以建立僅用於執行明確轉換或直接初始化的方便轉換，而不會導致安全的 Bool 問題所一例的問題種類。

Explicit 關鍵字可以套用至 c + + 98 之後的轉換**函**式，以及自 c + + 11 起的轉換函數。 下列各節包含如何使用**explicit**關鍵字的詳細資訊。

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>轉換構造函式

轉換建構函式可定義從使用者定義或內建類型轉換成使用者定義類型的作業。 下列範例示範從內建類型**double**轉換成使用者定義型別 `Money`的轉換函式。

```cpp
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

請注意，第一次呼叫函式 `display_balance` (採用類型 `Money` 的引數) 時不需要轉換，因為其引數是正確的類型。 不過，在第二次呼叫 `display_balance`時，需要進行轉換，因為引數的類型、值為 `49.95`的**double**不是函數所預期。 函式不能直接使用這個值，但因為從引數的類型轉換成相符參數的**類型（`Money`** ），所以類型 `Money` 的暫存值是從引數所構成，並用來完成函式呼叫。 在第三個 `display_balance`呼叫中，請注意，引數不是**double**，而是值為 `9.99`的**float** ，但仍可完成函式呼叫，因為編譯器可以執行標準轉換（在此案例中，從**float**到**double**），然後從 `Money` **double**執行使用者定義的轉換，以完成必要的轉換。

### <a name="declaring-conversion-constructors"></a>宣告轉換建構函式

下列規則適用於宣告轉換建構函式：

- 轉換的目標類型是所建構的使用者定義類型。

- 轉換建構函式通常只會採用一個引數，屬於此來源類型。 不過，如果其他每個參數都有預設值，轉換建構函式就可以指定其他參數。 來源類型仍是第一個參數的類型。

- 轉換建構函式就像所有建構函式一樣，並沒有指定傳回型別。 在宣告中指定傳回類型是一種錯誤。

- 轉換建構函式可以是明確的。

### <a name="explicit-conversion-constructors"></a>明確轉換建構函式

藉由將轉換的函式宣告為**明確**，它只能用來執行物件的直接初始化，或執行明確的轉換。 如此可以防止接受類別型別引數的函式，不會也隱含地接受轉換建構函式來源類型的引數，並防止類別類型從來源類型的值以複製的方式初始化。 下列範例示範如何定義明確的轉換建構函式，並示範它對何種程式碼產生格式正確的影響。

```cpp
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

在此範例中，請注意，您仍可使用明確的轉換建構函式來執行 `payable` 的直接初始化。 如果您要以複製方式初始化 `Money payable = 79.99;`，則會是個錯誤。 第一次呼叫 `display_balance` 時並不受影響，因為引數是正確的類型。 第二次呼叫 `display_balance` 時則是個錯誤，因為轉換建構函式不能用來執行隱含轉換。 `display_balance` 的第三個呼叫是合法的，因為明確轉型為 `Money`，但請注意，編譯器仍然會藉由將從**float**到**double**的隱含轉換插入，來協助完成轉換。

雖然允許隱含轉換的便利性很吸引人，但是這麼做會造成難以找出的 Bug。 經驗告訴我們，除非您確定想要讓特定的轉換隱含發生，否則最好是讓所有轉換建構函式都很明確。

##  <a name="conversion-functions"></a><a name="ConvFunc"></a>轉換函式

轉換函式可定義從使用者定義類型到其他類型的轉換作業。 這些函式有時候是指「轉型運算子」，因為當值轉型為不同類型時，會將其連同轉換建構函式一起呼叫。 下列範例示範的轉換函式，會從使用者自訂類型（`Money`）轉換成內建類型**double**：

```cpp
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

請注意，成員變數 `amount` 設為私用，而且會引進類型為**double**的公用轉換函式，以傳回 `amount`的值。 在函式 `display_balance` 中，使用資料流插入運算子 `balance` 將 `<<` 的值以資料流傳送至標準輸出時，會發生隱含轉換。 因為沒有為使用者定義型別定義資料流程插入運算子 `Money`，但內建型別為**double**，所以編譯器可以使用從 `Money` 到**double**的轉換函式來滿足資料流程插入運算子。

衍生類別會繼承轉換函式。 當衍生類別中的轉換函式轉換成完全相同的類型時，只會覆寫繼承的轉換函式。 例如，衍生類別**運算子 int**的使用者定義轉換函式不會覆寫（或甚至影響）基類**運算子**的使用者定義轉換函式，即使標準轉換定義**int**和**short**之間的轉換關聯性也一樣。

### <a name="declaring-conversion-functions"></a>宣告轉換函式

下列規則適用於宣告轉換函式：

- 必須先宣告轉換的目標類型，才能宣告轉換函式。 不能在轉換函式的宣告中宣告類別、結構、列舉和 typedef。

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- 轉換函式不接受引數。 在宣告中指定任何參數都是錯誤。

- 轉換函式具有以轉換函式名稱 (也是轉換的目標類型名稱) 指定的傳回型別。 在宣告中指定傳回類型是一種錯誤。

- 轉換函式可以是虛擬的。

- 轉換函式可以是明確的。

### <a name="explicit-conversion-functions"></a>明確轉換函數

當轉換函式宣告為明確時，就只能用來執行明確轉型。 如此可以防止接受轉換函式目標型別引數的函式，不會也隱含地接受類別類型的引數，並防止目標類型的執行個體從類別類型的值以複製方式初始化。 下列範例示範如何定義明確的轉換函式，並示範它對何種程式碼產生格式正確的影響。

```cpp
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

這裡的轉換函式**operator double**已明確完成，而且在函式中引進了明確轉換為**double**類型的 `display_balance` 來執行轉換。 如果省略此轉型，編譯器會找不到適合類型 `<<` 的資料流插入運算子 `Money`，並且會發生錯誤。
