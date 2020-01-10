---
title: 宣告和定義（C++）
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: d52294b635e05f42a4c48620214a90cad609f575
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301544"
---
# <a name="declarations-and-definitions-c"></a>宣告和定義（C++）

程式C++是由各種實體組成，例如變數、函式、類型和命名空間。 這些實體中的每個*都必須先行宣告才能使用*。 宣告會指定實體的唯一名稱，以及其類型和其他特性的相關資訊。 在C++宣告名稱的點，是編譯器可看見的位置點。 您不能參考在編譯單位稍後的某個時間點所宣告的函式或類別。 變數應該在使用的點之前，盡可能地宣告為接近。

下列範例顯示一些宣告：

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

在第5行上，會宣告 `main` 函式。 在第7行上，會宣告並*初始化*名為 `pi` 的**const**變數。 在第8行上，會使用函式 `f`所產生的值來宣告和初始化整數 `i`。 因為第3行的*向前*宣告，所以編譯器可以看到名稱 `f`。 

在第9行中，已宣告名為 `obj` 類型為 `C` 的變數。 不過，此宣告會引發錯誤，因為 `C` 在程式中稍後才會宣告，而且不會向前宣告。 若要修正錯誤，您可以在 `main` 之前移動 `C` 的整個*定義*，或為它新增正向宣告。 這種行為與其他語言（例如C#）不同，其中的函式和類別可以在來源檔案中的宣告點之前使用。 

在第10行中，會宣告名為 `str` 類型為 `std::string` 的變數。 `std::string` 的名稱是可見的，因為它是在 `string`[標頭檔](header-files-cpp.md)中引進，而該檔案會合並到第1行的原始程式檔中。 `std` 是宣告 `string` 類別的命名空間。

在第11行中，因為尚未宣告名稱 `j`，所以會引發錯誤。 宣告必須提供類型，與其他語言（例如 javaScript）不同。 在第12行中，會使用 `auto` 關鍵字，這會指示編譯器根據其初始化的值來推斷 `k` 的類型。 在此情況下，編譯器會為該類型選擇 `int`。  

## <a name="declaration-scope"></a>宣告範圍

宣告引進的名稱在宣告發生的*範圍*內是有效的。 在上述範例中，`main` 函式內宣告的變數是*區域變數*。 您可以在*全域範圍*外，宣告名為 `i` 的另一個變數，而且它會是完全不同的實體。 不過，這類名稱的重複可能會導致程式設計人員混淆和錯誤，應予以避免。 在第21行中，類別 `C` 是在命名空間 `N`的範圍中宣告。 使用命名空間有助於避免*名稱衝突*。 大部分C++的標準程式庫名稱都是在 `std` 命名空間內宣告。 如需範圍規則如何與宣告互動的詳細資訊，請參閱[範圍](../cpp/scope-visual-cpp.md)。

## <a name="definitions"></a>定義

某些實體（包括函式、類別、列舉和常數變數）除了要宣告外，還必須定義。 *定義*會在程式中稍後使用實體時，為編譯器提供產生機器碼所需的所有資訊。 在上述範例中，第3行包含函式 `f` 的宣告，但函數的*定義*是在第15到18行提供。 在第21行上，會宣告和定義類別 `C` （雖然定義的類別不會執行任何動作）。 常數變數必須在其宣告所在的相同語句中，以其他單字指派值的方式定義。 內建類型的宣告（例如 `int`）是自動定義的，因為編譯器知道要為它配置多少空間。

下列範例會顯示也是定義的宣告：

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

以下是一些不是定義的宣告：

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Typedef 和 using 語句

在舊版的C++中， [typedef](aliases-and-typedefs-cpp.md)關鍵字是用來宣告新名稱，這是另一個名稱的*別名*。 例如，類型 `std::string` 是 `std::basic_string<char>`的另一個名稱。 程式設計人員為何要使用 typedef 名稱，而不是實際名稱，這應該很明顯。 在新式C++中， [using](aliases-and-typedefs-cpp.md)關鍵字慣用於 typedef，但概念相同：已宣告並定義實體的新名稱。

## <a name="static-class-members"></a>靜態類別成員

因為靜態類別資料成員是由類別的所有物件共用的離散變數，所以必須在類別定義之外定義和初始化。 （如需詳細資訊，請參閱[類別](../cpp/classes-and-structs-cpp.md)）。

## <a name="extern-declarations"></a>extern 宣告

一個C++程式可能包含一個以上的[編譯單位](header-files-cpp.md)。 若要宣告在不同編譯單位中定義的實體，請使用[extern](extern-cpp.md)關鍵字。 宣告中的資訊足以用於編譯器，但如果在連結步驟中找不到實體的定義，則連結器會引發錯誤。

## <a name="in-this-section"></a>本節內容

[儲存類別](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[初始設定式](initializers.md)<br/>
[別名和 typedef](aliases-and-typedefs-cpp.md)<br/>
[using 宣告](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[中的屬性C++](attributes.md)<br/>

## <a name="see-also"></a>請參閱

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
