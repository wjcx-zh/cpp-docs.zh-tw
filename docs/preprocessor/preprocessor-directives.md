---
title: 前置處理器指示詞
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: ac765d33aec4795e94866c097d6c453dbd0e4a08
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845324"
---
# <a name="preprocessor-directives"></a>前置處理器指示詞

預處理器指示詞（例如 `#define` 和 `#ifdef` ）通常用來讓來來源程式在不同的執行環境中變得更容易變更和編譯。 來源檔案中的指示詞會指示預處理器採取特定動作。 例如，前置處理器可以取代文字中的語彙基元、將其他檔案的內容插入原始程式檔，或是透過移除文字區段來隱藏編譯檔案的一部分。 在巨集展開之前，會辨識並執行前置處理器程式行。 因此，如果宏擴充到看起來像預處理器命令的內容，則預處理器無法辨識它。

預處理器語句使用的字元集與原始程式檔語句相同，但不支援 escape 序列。 前置處理器陳述式中使用的字元集與執行字元集相同。 前置處理器也會辨識負數字元值。

前置處理器會辨識下列指示詞：

:::row:::
   :::column span="":::
      [`#define`](../preprocessor/hash-define-directive-c-cpp.md)\
      [`#elif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#else`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#endif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#error`](../preprocessor/hash-error-directive-c-cpp.md)\
      [`#if`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#ifdef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)\
      [`#ifndef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#import`](../preprocessor/hash-import-directive-cpp.md)\
      [`#include`](../preprocessor/hash-include-directive-c-cpp.md)\
      [`#line`](../preprocessor/hash-line-directive-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#pragma`](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
      [`#undef`](../preprocessor/hash-undef-directive-c-cpp.md)\
      [`#using`](../preprocessor/hash-using-directive-cpp.md)
   :::column-end:::
:::row-end:::

數位記號 (`#`) 必須是包含指示詞的行上的第一個非空白字元空白字元。 空白字元可以出現在數位記號和指示詞的第一個字母之間。 某些指示詞會包含引數或值。 指示詞後面的任何文字 (除了屬於指示詞一部分的引數或值以外，) 前面必須加上單行批註分隔符號 (`//`) 或在批註分隔符號 () 中括住 `/* */` 。 包含預處理器指示詞的行，可以透過反斜線 () 來繼續 `\` 。

預處理器指示詞可以出現在原始程式檔中的任何位置，但它們只適用于原始程式檔的其餘部分（在它們出現後）。

## <a name="see-also"></a>另請參閱

[預處理器運算子](../preprocessor/preprocessor-operators.md)\
[預先定義的宏](../preprocessor/predefined-macros.md)\
[c/c + + 預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
