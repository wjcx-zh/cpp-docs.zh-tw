---
title: 評估 Catch 區塊的方式 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 21d68b25fa3695a9b5637dcace081424f99911d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188098"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>評估 Catch 區塊的方式 (C++)

C++ 可讓您擲回任何類型的例外狀況，不過，一般建議擲回衍生自 std::exception 的類型。 指定與所擲回 **`catch`** 例外狀況相同類型的處理常式，或可攔截任何例外狀況類型的處理常式，可能會捕捉到 c + + 例外狀況。

如果擲回的例外狀況類型是類別，而該類別同時擁有一個或多個基底類別，則可以使用接受例外狀況類型的基底類別，以及接受例外狀況類型之基底參考的處理常式攔截例外狀況。 請注意，如果是以參考攔截例外狀況，它會繫結程序至實際擲回的例外狀況物件，否則它會是複本 (就如同函式的引數)。

當擲回例外狀況時，可能會由下列類型的 **`catch`** 處理常式攔截到：

- 可以接受任何類型的處理常式 (使用省略語法)。

- 接受與例外狀況物件相同類型的處理常式;由於它是複本，因此 **`const`** 會忽略和修飾詞 **`volatile`** 。

- 可以接受與例外狀況物件相同類型之參考的處理常式。

- 接受與 **`const`** **`volatile`** 例外狀況物件相同類型之或形式參考的處理常式。

- 接受與例外狀況物件相同類型之基類的處理常式;由於它是複本， **`const`** 因此會忽略和修飾詞 **`volatile`** 。 **`catch`** 基類的處理常式不能在 **`catch`** 衍生類別的處理常式之前。

- 可以接受與例外狀況物件相同類型的基底類別之參考的處理常式。

- 處理常式，可接受與例外狀況 **`const`** **`volatile`** 物件相同類型之基類或形式的參考。

- 可以接受指標的處理常式，擲回的指標物件可以透過標準指標轉換規則轉換成該指標。

**`catch`** 處理常式出現的順序很重要，因為指定區塊的處理常式 **`try`** 會依其外觀的順序進行檢查。 例如，將基底類別的處理常式放在衍生類別的處理常式前面就是錯誤的範例。 找到相符的 **`catch`** 處理常式之後，就不會檢查後續的處理常式。 因此，省略號 **`catch`** 處理常式必須是其區塊的最後一個處理常式 **`try`** 。 例如：

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

在此範例中，省略號 **`catch`** 處理常式是唯一檢查的處理常式。

## <a name="see-also"></a>另請參閱

[適用于例外狀況和錯誤處理的新式 c + + 最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)
