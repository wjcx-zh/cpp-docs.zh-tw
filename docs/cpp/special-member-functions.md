---
title: 特殊成員函式
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: 3b26628fd18749bd19819fe787888fd3264a79d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535755"
---
# <a name="special-member-functions"></a>特殊成員函式

*特殊成員函式*是類別 （或結構），在某些情況下，編譯器會自動為您產生的成員函式。 這些函式[預設建構函式](constructors-cpp.md#default_constructors)，則[解構函式](destructors-cpp.md)，則[複製建構函式和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)，和[移動建構函式和移動指派運算子](move-constructors-and-move-assignment-operators-cpp.md)。 如果您的類別未定義一或多個特殊成員函式，則編譯器可能會隱含地宣告並定義所使用的函式。 編譯器所產生的實作會呼叫*預設*特殊成員函式。 編譯器不會產生函式，如果不需要它們。

您可以使用，以明確宣告的預設特殊成員函式 **= default**關鍵字。 這可讓編譯器定義才有需要在相同的方式如同不完全宣告的函式的函式。

在某些情況下，編譯器可能會產生*刪除*特殊成員函式，都不是已定義且因此不可以呼叫。 在其中呼叫特定的特殊成員函式類別上沒有意義，指定類別的其他屬性的情況下，這可能會發生。 若要明確地防止自動產生特殊成員函式，您可以將它宣告為使用已刪除 **= 刪除**關鍵字。

編譯器會產生*預設建構函式*，只有在您未宣告任何其他建構函式時，才會採用任何引數，建構函式。 如果您宣告僅參數建構函式時，嘗試呼叫預設建構函式的程式碼會導致編譯器產生的錯誤訊息。 編譯器產生的預設建構函式會執行簡單 member-wise[預設會初始化](initializers.md#default_initialization)的物件。 預設初始化離開處於不定狀態的所有成員變數。

預設解構函式會執行物件的成員解構。 只有當基底類別解構函式是虛擬的它是虛擬的。

預設複製和移動建構函式和指派作業執行成員的位元模式複製或移動的非靜態資料成員。 移動宣告任何解構函式或移動或複製作業時，才會產生作業。 宣告沒有複製建構函式時，才會產生預設複製建構函式。 它會隱含地刪除如果宣告在移動作業。 只有在沒有複製指派運算子已明確宣告時，會產生預設複製指派運算子。 它會隱含地刪除如果宣告在移動作業。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](cpp-language-reference.md)