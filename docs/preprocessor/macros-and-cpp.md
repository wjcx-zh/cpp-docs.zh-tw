---
title: 巨集和 C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220796"
---
# <a name="macros-and-c"></a>巨集和 C++

C++提供新的功能, 其中有些會取代 ANSI C 預處理器所提供的功能。 這些新功能可強化此語言的類型安全及可預測性：

- 在C++中, 宣告為**const**的物件可以在常數運算式中使用。 它可讓程式宣告具有型別和值資訊的常數。 它們可以宣告可透過偵錯工具以透過符號的列舉。 當您使用預處理器`#define`指示詞來定義常數時, 它不會是精確的, 而不是型別安全。 除非套裝程式含接受其位址的運算式, 否則不會為**const**物件配置任何儲存體。

- C++ 內嵌函式功能取代了函式類型的巨集。 在巨集中使用內嵌函式的優點包括：

  - 類型安全。 內嵌函式的類型檢查限制與一般函式相同。 宏不是型別安全。

  - 修正具有副作用的引數處理。 內嵌函式會在輸入函數主體之前, 評估當做引數提供的運算式。 因此, 沒有機會具有副作用的運算式也不安全。

如需內嵌函數的詳細資訊, 請參閱[inline、 \___inline、_forceinline](../cpp/inline-functions-cpp.md)。

為了提供回溯相容性，Microsoft C++ 會保留存在於 ANSI C 和舊版 C++ 規格中的所有前置處理器功能。

## <a name="see-also"></a>另請參閱

[預先定義的宏](../preprocessor/predefined-macros.md)\
[巨集 (C/C++)](../preprocessor/macros-c-cpp.md)
