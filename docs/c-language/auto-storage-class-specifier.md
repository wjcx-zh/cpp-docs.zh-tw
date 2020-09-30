---
title: auto 儲存類別指定名稱
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 7f70ee1944e07ebcbd32b8110eee27fa6631be63
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509311"
---
# <a name="auto-storage-class-specifier"></a>`auto` 儲存類別規範

**`auto`** 儲存類別規範會宣告自動變數，也就是具有本機存留期的變數。 **`auto`** 變數只會顯示在其宣告所在的區塊中。 變數的宣告 **`auto`** 可以包含初始化運算式，如 [初始化](../c-language/initialization.md)中所述。 由於具有 **`auto`** 儲存類別的變數不會自動初始化，因此您應該在宣告這些變數時明確地將它們初始化，或在區塊內的語句中指派初始值。 未初始化的 **`auto`** 變數值為未定義。 **`auto`** **`register`** 如果指定了初始化運算式，就會在每次進入範圍時初始化或儲存類別 (的本機變數。 ) 

內部 **`static`** 變數 (具有本機或區塊範圍的靜態變數) 可以用任何外部或專案的位址初始化 **`static`** ，但無法使用其他專案的位址初始化， **`auto`** 因為專案的位址不是 **`auto`** 常數。

## <a name="see-also"></a>另請參閱

[`auto` 關鍵 字](../cpp/auto-cpp.md)
