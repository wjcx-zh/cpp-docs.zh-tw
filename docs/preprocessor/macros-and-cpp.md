---
title: 巨集和 C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 3b8721644e49a8bd289939d216c233da3286fd0a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219400"
---
# <a name="macros-and-c"></a>巨集和 C++

C + + 提供新的功能，其中一些會取代 ANSI C 預處理器所提供的功能。 這些新功能可強化此語言的類型安全及可預測性：

- 在 c + + 中，宣告為的物件 **`const`** 可以在常數運算式中使用。 它可讓程式宣告具有型別和值資訊的常數。 它們可以宣告可透過偵錯工具以透過符號的列舉。 當您使用預處理器指示詞 `#define` 來定義常數時，它不會是精確的，而不是型別安全。 **`const`** 除非該套裝程式含接受其位址的運算式，否則不會為物件配置任何儲存體。

- C++ 內嵌函式功能取代了函式類型的巨集。 在巨集中使用內嵌函式的優點包括：

  - 類型安全。 內嵌函式的類型檢查限制與一般函式相同。 宏不是型別安全。

  - 修正具有副作用的引數處理。 內嵌函式會在輸入函數主體之前，評估當做引數提供的運算式。 因此，沒有機會具有副作用的運算式也不安全。

如需內嵌函數的詳細資訊，請參閱[inline、__inline、 \_ _forceinline](../cpp/inline-functions-cpp.md)。

為了提供回溯相容性，Microsoft C++ 會保留存在於 ANSI C 和舊版 C++ 規格中的所有前置處理器功能。

## <a name="see-also"></a>另請參閱

[預先定義的宏](../preprocessor/predefined-macros.md)\
[巨集 (C/C++)](../preprocessor/macros-c-cpp.md)
