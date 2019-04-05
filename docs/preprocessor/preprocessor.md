---
title: 前置處理器
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: b1443d88fdba470cb8ed5058c9a9012bfbdc5bc7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028570"
---
# <a name="preprocessor"></a>前置處理器
前置處理器是文字處理器，會在轉譯的第一個階段操作原始程式檔的文字。 前置處理器不會剖析原始程式文字，但會將原始程式文字分解為用於尋找巨集呼叫的語彙基元。 雖然編譯器通常在第一次傳遞時叫用前置處理器，但也可以分別叫用前置處理器，在不進行編譯的情況下處理文字。

有關前置處理器的參考資料包含下列章節：

- [前置處理器指示詞](../preprocessor/preprocessor-directives.md)

- [前置處理器運算子](../preprocessor/preprocessor-operators.md)

- [預先定義巨集](../preprocessor/predefined-macros.md)

- [Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft 特定的**

您可以取得您的程式碼使用前置處理後的清單[/E](../build/reference/e-preprocess-to-stdout.md)或是[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)編譯器選項。 兩個選項均會叫用前置處理器，並將產生的文字輸出到標準輸出裝置 (通常是主控台)。 這兩個選項之間的差異是 /E 包括 `#line` 指示詞，而 /EP 則會刪除這些指示詞。

**END Microsoft 特定的**

##  <a name="_predir_special_terminology"></a> 特殊術語

在前置處理器文件中，「引數」一詞是指傳遞至函式的實體。 某些情況下，會以「實際」或「型式」修飾「引數」一詞，分別用於說明函式呼叫中指定的引數運算式，以及函式定義中指定的引數宣告。

「變數」一詞是指簡單的 C 類型資料物件。 「物件」一詞是指 C++ 物件和變數；屬於內含的詞彙。

## <a name="see-also"></a>另請參閱

[C/C++ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[轉譯階段](../preprocessor/phases-of-translation.md)