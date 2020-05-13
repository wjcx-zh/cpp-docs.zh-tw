---
title: 前置處理器
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337496"
---
# <a name="preprocessor"></a>前置處理器

前置處理器是文字處理器，會在轉譯的第一個階段操作原始程式檔的文字。 預處理器不解析源文本,但它確實將其分解為令牌以查找宏調用。 雖然編譯器通常在第一次傳遞時叫用前置處理器，但也可以分別叫用前置處理器，在不進行編譯的情況下處理文字。

有關前置處理器的參考資料包含下列章節：

- [前置處理器指示詞](../preprocessor/preprocessor-directives.md)

- [前置處理器運算子](../preprocessor/preprocessor-operators.md)

- [預先定義的巨集](../preprocessor/predefined-macros.md)

- [Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft 特定的**

您可以使用[/E](../build/reference/e-preprocess-to-stdout.md)或[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)編譯器選項在預處理後獲取原始碼的清單。 這兩個選項都調用預處理器並將生成的文本發送到標準輸出設備,在大多數情況下,標準輸出設備是控制台。 這兩個選項之間的區別在於包含`/E``#line`指令,`/EP`並剝離這些指令。

**結束微軟的**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>特殊字詞

在前置處理器文件中，「引數」一詞是指傳遞至函式的實體。 在某些情況下,它由"實際"或"正式"修改,分別描述函數調用中指定的參數表達式和函數定義中指定的參數聲明。

「變數」一詞是指簡單的 C 類型資料物件。 術語「物件」是指C++物件和變數;這是一個包容性的術語。

## <a name="see-also"></a>另請參閱

[C/C++預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)\
[翻譯階段](../preprocessor/phases-of-translation.md)
