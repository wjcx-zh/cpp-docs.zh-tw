---
title: C/C++ 前置處理器參考
description: Visual Studio 中的 Microsoft C/c + + 編譯器預處理器參考。
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e72146d8b88f5a4bffcaaa121f6851d740ec948b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075630"
---
# <a name="cc-preprocessor-reference"></a>C/C++ 前置處理器參考

*C/c + + 預處理器參考*會說明在 Microsoft C/c + + 中執行預處理器的程式。 前置處理器會先對 C 和 C++ 檔案執行初步作業，再將檔案傳遞至編譯器。 您可以使用前置處理器，有條件地編譯程式碼、插入檔案、指定編譯時間錯誤訊息，以及將電腦特定規則加入至程式碼區段。

在 Visual Studio 2019 中， [/zc：預處理器](../build/reference/zc-preprocessor.md) 編譯器選項提供完全一致的 C11 和 C17 預處理器。 這是使用編譯器旗標或時的預設 `/std:c11` 值 `/std:c17` 。

## <a name="in-this-section"></a>本節內容

[預處理](preprocessor.md)\
提供傳統和新的符合預處理器的總覽。

[預處理器指示詞](../preprocessor/preprocessor-directives.md)\
描述指示詞，通常用來使原始程式易於變更，以及在不同的執行環境中易於編譯。

[預處理器運算子](../preprocessor/preprocessor-operators.md)\
討論 `#define` 指示詞的內容中所使用的四個前置處理器特定運算子。

[預先定義的宏](../preprocessor/predefined-macros.md)\
討論 C 和 c + + 標準和 Microsoft c + + 所指定的預先定義宏。

[Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
討論 pragma，它讓每個編譯器可以提供電腦和作業系統專屬功能，同時還能保留與 C 及 C++ 語言的整體相容性。

## <a name="related-sections"></a>相關章節

[C + + 語言參考](../cpp/cpp-language-reference.md)\
為 C++ 語言的 Microsoft 實作提供參考資料。

[C 語言參考](../c-language/c-language-reference.md)\
為 C 語言的 Microsoft 實作提供參考資料。

[C/c + + 組建參考](../build/reference/c-cpp-building-reference.md)\
提供討論編譯器和連結器選項的主題連結。

[Visual Studio 專案-c + +](../build/creating-and-managing-visual-cpp-projects.md)\
說明 Visual Studio 使用者介面，可讓您指定專案系統將搜尋的目錄，以尋找您的 C++ 專案的檔案。
