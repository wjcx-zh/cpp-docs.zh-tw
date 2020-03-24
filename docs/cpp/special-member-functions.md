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
ms.openlocfilehash: b15a0e50774bbc4e70912a31f9a57ea0439f2c12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178687"
---
# <a name="special-member-functions"></a>特殊成員函式

*特殊成員*函式是類別（或結構）成員函式，在某些情況下，編譯器會自動為您產生。 這些函數是[預設](constructors-cpp.md#default_constructors)的[函](destructors-cpp.md)式、「析構函數」、「複製」「作業」[和「複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)」，以及「移動」和「[移動指派運算子](move-constructors-and-move-assignment-operators-cpp.md)」。 如果您的類別未定義一或多個特殊成員函式，則編譯器可能會隱含宣告並定義所使用的函數。 編譯器產生的實*值稱為預設*的特殊成員函式。 如果不需要，編譯器不會產生函數。

您可以使用 **= default**關鍵字，明確宣告預設的特殊成員函式。 如此一來，編譯器就只會在必要時定義函式，就像函式完全沒有宣告一樣。

在某些情況下，編譯器可能會產生*已刪除*的特殊成員函式，這些函式尚未定義，因此無法呼叫。 如果類別的其他屬性在類別上呼叫特定特殊成員函式沒有意義，就可能發生這種情況。 若要明確避免自動產生特殊成員函式，您可以使用 **= delete**關鍵字將它宣告為 deleted。

編譯器會產生*預設*的函式，也就是不使用任何引數的函式，只有在您尚未宣告任何其他的函式時。 如果您只宣告了接受參數的函式，則嘗試呼叫預設的函式的程式碼會導致編譯器產生錯誤訊息。 編譯器產生的預設函式會針對物件執行簡單的成員[預設初始化](initializers.md#default_initialization)。 預設初始化會將所有成員變數保留為不定狀態。

預設的析構函式會執行物件的成員的析構。 只有當基類的析構函式為虛擬時，它才會是虛擬的。

預設的複製和移動結構和指派作業會執行成員取向的位模式複製或非靜態資料成員的移動。 只有在未宣告任何析構函數或移動或複製作業時，才會產生移動作業。 只有在未宣告任何複製的函式時，才會產生預設的複製函數。 如果已宣告移動作業，則會隱含地刪除它。 只有在未明確宣告任何複製指派運算子時，才會產生預設複製指派運算子。 如果已宣告移動作業，則會隱含地刪除它。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](cpp-language-reference.md)
