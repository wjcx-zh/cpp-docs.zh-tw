---
title: 批註（C++）
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: 3326ad7d0b5118182a5d582061fd0c103986f232
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189750"
---
# <a name="comments-c"></a>批註（C++）

註解是會被編譯器忽略，但對程式設計人員而言很有用的文字。 註解通常用來標註程式碼供未來參考。 編譯器會將它們視為空白字元。 您可以使用測試中的批註，讓特定的程式程式碼處於非使用中狀態;不過，`#if`/`#endif` 預處理器指示詞的效果更好，因為您可以圍繞包含批註的程式碼，但無法嵌套批註。

C++ 註解以下列其中一種方式撰寫：

- `/*` (斜線、星號) 字元，後面接著任何字元序列 (包括新行)，後面接著 `*/` 字元。 這語法與 ANSI C 相同。

- `//` (兩個斜線) 字元，後面接著任何字元序列。 一個沒有前置反斜線的新行會終止這種形式的註解。 因此，它通常稱為「單行註解」。

註解字元 (`/*`、`*/` 和 `//`) 在字元常數、字串常值或註解中沒有特殊意義。 因此，使用第一種語法的註解不可以是巢狀。

## <a name="see-also"></a>另請參閱

[語彙慣例](../cpp/lexical-conventions.md)
