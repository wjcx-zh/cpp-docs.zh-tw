---
title: 前置處理器運算子
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 5dd252fb495a05efe6eef45674f9ecd601a298a7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857940"
---
# <a name="preprocessor-operators"></a>前置處理器運算子

`#define` 指示詞的內容中會使用四個預處理器特定的運算子。 請參閱下表以取得每個的摘要。 字串化、字元化和語彙基元帶入運算子在下面三節中討論。 如需 `defined` 運算子的詳細資訊，請參閱[#if、#elif、#else 和 #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)指示詞。

|運算子|動作|
|--------------|------------|
|[字串化運算子（#）](../preprocessor/stringizing-operator-hash.md)|使對應的實際引數以雙引號括住|
|[字元化運算子（# @）](../preprocessor/charizing-operator-hash-at.md)|使對應的引數以單引號括住，並被視為字元（Microsoft 專有）|
|[標記貼入的運算子（# #）](../preprocessor/token-pasting-operator-hash-hash.md)|允許做為實際引數的語彙基元串連，形成其他語彙基元|
|[定義的運算子](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|簡化某些巨集指示詞中複合運算式的撰寫|

## <a name="see-also"></a>請參閱

[預處理器](../preprocessor/preprocessor-directives.md)指示詞\
[預先定義的宏](../preprocessor/predefined-macros.md)\
[c/c + + 預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
