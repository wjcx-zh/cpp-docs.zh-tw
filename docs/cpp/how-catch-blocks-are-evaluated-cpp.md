---
title: Catch 區塊的方式進行評估 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe86770692554551b88e1aef9bbddc509e21f0f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039435"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>評估 Catch 區塊的方式 (C++)

C++ 可讓您擲回任何類型的例外狀況，不過，一般建議擲回衍生自 std::exception 的類型。 ，就可以攔截 c + + 例外狀況**攔截**指定相同的型別，擲回的例外狀況，或由可攔截任何類型的例外狀況處理常式的處理常式。

如果擲回的例外狀況類型是類別，而該類別同時擁有一個或多個基底類別，則可以使用接受例外狀況類型的基底類別，以及接受例外狀況類型之基底參考的處理常式攔截例外狀況。 請注意，如果是以參考攔截例外狀況，它會繫結程序至實際擲回的例外狀況物件，否則它會是複本 (就如同函式的引數)。

擲回例外狀況時，它可能會抓到下列類型的所**攔截**處理常式：

- 可以接受任何類型的處理常式 (使用省略語法)。

- 接受與例外狀況物件相同類型的處理常式它是複本，因為**const**並**volatile**修飾詞會被忽略。

- 可以接受與例外狀況物件相同類型之參考的處理常式。

- 接受參考的處理常式**const**或是**volatile**形式的例外狀況物件相同的型別。

- 接受與例外狀況物件相同型別的基底類別的處理常式它是複本，因為**const**並**volatile**修飾詞會被忽略。 **攔截**基底類別處理常式必須前面**攔截**衍生的類別處理常式。

- 可以接受與例外狀況物件相同類型的基底類別之參考的處理常式。

- 接受參考的處理常式**const**或是**volatile**形式的例外狀況物件相同類型的基底類別。

- 可以接受指標的處理常式，擲回的指標物件可以透過標準指標轉換規則轉換成該指標。

順序**攔截**處理常式會出現很重要，因為處理常式指定**嘗試**區塊會檢查其出現的順序。 例如，將基底類別的處理常式放在衍生類別的處理常式前面就是錯誤的範例。 之後的相符**攔截**找到處理常式，就不會檢查後續處理常式。 如此一來，省略符號**攔截**處理常式必須是最後一個處理常式，如其**嘗試**區塊。 例如: 

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

在此範例中，省略符號**攔截**處理常式是唯一會進行檢查的處理常式。

## <a name="see-also"></a>另請參閱

[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)