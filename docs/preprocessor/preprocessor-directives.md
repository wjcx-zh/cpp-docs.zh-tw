---
title: 前置處理器指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2976feebf4a17465c2bf2010b4dc608550ce077
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059463"
---
# <a name="preprocessor-directives"></a>前置處理器指示詞

前置處理器指示詞，例如`#define`和`#ifdef`，通常用來使原始程式易於變更和易於編譯在不同的執行環境中。 原始程式檔中的指示詞會指示前置處理器執行特定動作。 例如，前置處理器可以取代文字中的語彙基元、將其他檔案的內容插入原始程式檔，或是透過移除文字區段來隱藏編譯檔案的一部分。 在巨集展開之前，會辨識並執行前置處理器程式行。 因此，如果巨集展開成類似前置處理器命令的程式碼，前置處理器就無法辨識該命令。

除了不支援逸出序列以外，前置處理器陳述式使用的字元集與原始程式檔陳述式使用的相同。 前置處理器陳述式中使用的字元集與執行字元集相同。 前置處理器也會辨識負數字元值。

前置處理器會辨識下列指示詞：

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

數字符號 (**#**) 必須是包含指示詞; 該行的第一個非空白字元泛空白字元可以出現數字符號和指示詞的第一個字母之間。 某些指示詞會包含引數或值。 （除外的引數或值，是在指示詞的一部分） 指示詞後面的任何文字前面必須有單行註解分隔符號 (**//**) 或註解分隔符號括住 ( __/\*\*/__). 包含前置處理器指示詞的行可以繼續的前面加上反斜線的行結尾標記 (**\\**)。

前置處理器指示詞可以出現在原始程式檔的任何位置，但是這只會套用至原始程式檔的其餘部分。

## <a name="see-also"></a>另請參閱

[前置處理器運算子](../preprocessor/preprocessor-operators.md)<br/>
[預先定義的巨集](../preprocessor/predefined-macros.md)<br/>
[C/C++ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
