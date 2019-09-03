---
title: 前置處理器
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 883504810f1b659e28764a75ebc7cfda325920a5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222229"
---
# <a name="preprocessor"></a>前置處理器

前置處理器是文字處理器，會在轉譯的第一個階段操作原始程式檔的文字。 預處理器不會剖析來源文字, 但會將它分解成標記來尋找宏呼叫。 雖然編譯器通常在第一次傳遞時叫用前置處理器，但也可以分別叫用前置處理器，在不進行編譯的情況下處理文字。

有關前置處理器的參考資料包含下列章節：

- [預處理器指示詞](../preprocessor/preprocessor-directives.md)

- [預處理器運算子](../preprocessor/preprocessor-operators.md)

- [預先定義巨集](../preprocessor/predefined-macros.md)

- [Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft 專屬**

您可以使用[/e](../build/reference/e-preprocess-to-stdout.md)或[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)編譯器選項, 在前置處理之後取得原始程式碼的清單。 這兩個選項都會叫用預處理器, 並將產生的文字傳送到標準輸出裝置, 在大多數情況下, 這是主控台。 這兩個選項之間的差異在於`/E`包括`#line`指示詞, `/EP`並去除這些指示詞。

**結束 Microsoft 專屬**

##  <a name="_predir_special_terminology"></a>特殊術語

在前置處理器文件中，「引數」一詞是指傳遞至函式的實體。 在某些情況下, 它是由「實際」或「正式」修改, 其中描述在函式呼叫中指定的引數運算式, 以及在函式定義中指定的引數宣告。

「變數」一詞是指簡單的 C 類型資料物件。 「物件」一詞指的是C++物件和變數;這是內含詞彙。

## <a name="see-also"></a>另請參閱

[C/C++預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)\
[翻譯階段](../preprocessor/phases-of-translation.md)
