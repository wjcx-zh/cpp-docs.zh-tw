---
title: 前置處理器運算子
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 0b105cc2039e2aa50c11b796e5474a97d8c5c702
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035685"
---
# <a name="preprocessor-operators"></a>前置處理器運算子
`#define` 指示詞的內容中使用四個前置處理器特定運算子 (請參閱下列清單以取得每一個運算子的摘要)。 字串化、字元化和語彙基元帶入運算子在下面三節中討論。 如需`defined`運算子，請參閱[#if、 #elif、 #else 和 #endif 指示詞](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。

|運算子|動作|
|--------------|------------|
|[字串化運算子 （#）](../preprocessor/stringizing-operator-hash.md)|使對應的實際引數以雙引號括住|
|[字元化運算子 (#@)](../preprocessor/charizing-operator-hash-at.md)|使對應的引數以單引號括住並視為字元 (Microsoft 專用)|
|[語彙基元帶入的運算子 （# #）](../preprocessor/token-pasting-operator-hash-hash.md)|允許做為實際引數的語彙基元串連，形成其他語彙基元|
|[已定義的運算子](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|簡化某些巨集指示詞中複合運算式的撰寫|

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)<br/>
[預先定義的巨集](../preprocessor/predefined-macros.md)<br/>
[C/C++ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)