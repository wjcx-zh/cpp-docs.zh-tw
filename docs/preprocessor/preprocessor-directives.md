---
title: 前置處理器指示詞
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: 86432ebf210523dd958f3258075d9e9c6d3bb4e6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222273"
---
# <a name="preprocessor-directives"></a>前置處理器指示詞

預處理器指示詞 ( `#define`例如`#ifdef`和) 通常用來使來源程式在不同的執行環境中易於變更和輕鬆地進行編譯。 原始程式檔中的指示詞會告訴預處理器採取特定動作。 例如，前置處理器可以取代文字中的語彙基元、將其他檔案的內容插入原始程式檔，或是透過移除文字區段來隱藏編譯檔案的一部分。 在巨集展開之前，會辨識並執行前置處理器程式行。 因此, 如果宏展開為類似預處理器命令的專案, 則預處理器無法辨識它。

預處理器語句使用的字元集與原始程式檔語句相同, 但不支援 escape 序列。 前置處理器陳述式中使用的字元集與執行字元集相同。 前置處理器也會辨識負數字元值。

前置處理器會辨識下列指示詞：

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

數位記號 (`#`) 必須是包含指示詞之行上的第一個非空白字元空白字元。 空白字元可以出現在數位記號和指示詞的第一個字母之間。 某些指示詞會包含引數或值。 指示詞後面的任何文字 (引數或屬於指示詞的值除外) 都必須在單行批註分隔符號 (`//`) 之前, 或以批註分隔符號 (`/* */`) 括住。 包含預處理器指示詞的程式程式碼, 可以使用反斜線 (`\`) 緊接在行尾標記的前面繼續。

預處理器指示詞可以出現在原始程式檔中的任何位置, 但它們在出現之後, 只會套用至原始程式檔的其餘部分。

## <a name="see-also"></a>另請參閱

[預處理器運算子](../preprocessor/preprocessor-operators.md)\
[預先定義的宏](../preprocessor/predefined-macros.md)\
[c/c + + 預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
