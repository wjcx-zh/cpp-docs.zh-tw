---
title: 巨集 (C/C++)
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: ba2c0f012974a528876219d00c61c0f31a6cd820
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218856"
---
# <a name="macros-cc"></a>巨集 (C/C++)

預處理器會展開所有程式列中的宏, 但*預處理器*指示 **#** 詞除外, 具有做為第一個非空白字元的行。 它會在某些指示詞的部分中展開宏, 而不會略過做為條件式編譯的一部分。 *條件式編譯*指示詞可讓您隱藏原始檔部分的編譯。 它們會測試常數運算式或識別碼, 以判斷要傳遞給編譯器的文字區塊, 以及在前置處理期間要從原始檔移除哪些文字。

`#define` 指示詞通常用於讓有意義的識別項與常數、關鍵字和常用的陳述式或運算式產生關聯。 代表常數的識別碼有時稱為*符號常數*或*資訊清單常數*。 代表語句或運算式的識別碼稱為「*宏*」。 這份前置處理器文件中只會使用「巨集」這個詞彙。

當程式來源文字或特定其他預處理器命令的引數中辨識宏的名稱時, 它會被視為對該宏的呼叫。 巨集名稱會以巨集主體的複本取代。 如果巨集接受引數，巨集名稱後面的實際引數就會取代巨集主體中的正式參數。 以已處理的主體複本取代宏呼叫的程式稱為「*擴充*」宏呼叫。

實際上，巨集分成兩種類型。 *類似物件的*宏不接受引數。 *類似函式的*宏可以定義為接受引數, 使其外觀和作用就像函式呼叫。 因為宏不會產生實際的函式呼叫, 所以您可以使用宏取代函式呼叫, 讓程式執行的速度更快。 (在 C++ 中，內嵌函式通常是慣用方法)。不過, 如果您不小心定義和使用宏, 則可能會造成問題。 您可能需要在具有引數的巨集定義中使用括號，以保持運算式中的適當優先順序。 此外，巨集也可能無法正確處理具有副作用的運算式。 如需詳細資訊, 請`getrandom`參閱[#define](../preprocessor/hash-define-directive-c-cpp.md)指示詞中的範例。

定義宏之後, 您就無法將它重新定義為不同的值, 而不需要先移除原始定義。 不過，您可以用完全相同的定義重新定義巨集。 因此, 相同的定義可能會在程式中出現一次以上。

`#undef`指示詞會移除宏的定義。 移除定義之後, 您可以將宏重新定義為不同的值。 [#Define](../preprocessor/hash-define-directive-c-cpp.md)指示詞和[#undef](../preprocessor/hash-undef-directive-c-cpp.md)指示詞會分別`#define`討論`#undef`和指示詞。

如需詳細資訊，請參閱：

- [巨集和 C++](../preprocessor/macros-and-cpp.md)

- [Variadic 巨集](../preprocessor/variadic-macros.md)

- [預先定義巨集](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>另請參閱

[C/C++預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
