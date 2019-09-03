---
title: 前置處理器運算子
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 1c556e4af5913ba8d0dc7efc9648e0d0004d9d7e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222245"
---
# <a name="preprocessor-operators"></a>前置處理器運算子

指示詞的內容`#define`中會使用四個預處理器特定的運算子。 請參閱下表以取得每個的摘要。 字串化、字元化和語彙基元帶入運算子在下面三節中討論。 如需`defined`運算子的詳細資訊, 請參閱[#if、#elif、#else 和 #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)指示詞。

|運算子|動作|
|--------------|------------|
|[字串化運算子 (#)](../preprocessor/stringizing-operator-hash.md)|使對應的實際引數以雙引號括住|
|[字元化運算子 (# @)](../preprocessor/charizing-operator-hash-at.md)|使對應的引數以單引號括住並視為字元 (Microsoft 專用)|
|[標記貼入的運算子 (# #)](../preprocessor/token-pasting-operator-hash-hash.md)|允許做為實際引數的語彙基元串連，形成其他語彙基元|
|[定義的運算子](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|簡化某些巨集指示詞中複合運算式的撰寫|

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)\
[預先定義的宏](../preprocessor/predefined-macros.md)\
[c/c + + 預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
