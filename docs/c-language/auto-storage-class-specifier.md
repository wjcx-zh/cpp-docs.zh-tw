---
title: auto 儲存類別指定名稱
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: e39b37e2dc91dce31b6871d721875c75b8ebd629
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223755"
---
# <a name="auto-storage-class-specifier"></a>`auto`儲存類別規範

**`auto`** 儲存類別規範會宣告自動變數，也就是具有本機存留期的變數。 **`auto`** 變數只有在其宣告所在的區塊中才可見。 變數的宣告 **`auto`** 可以包含初始化運算式，如[初始化](../c-language/initialization.md)中所述。 由於具有 **`auto`** 儲存類別的變數不會自動初始化，因此您應該在宣告它們時明確初始化它們，或在區塊內的語句中指派初始值。 未初始化的 **`auto`** 變數值為未定義。 （ **`auto`** **`register`** 如果指定了初始化運算式，則會在每次進入範圍時初始化或儲存類別的本機變數）。

內部 **`static`** 變數（具有本機或區塊範圍的靜態變數）可以使用任何外部或專案的位址進行初始化 **`static`** ，但不能以另一個專案的位址初始化， **`auto`** 因為專案的位址 **`auto`** 不是常數。

## <a name="see-also"></a>另請參閱

[`auto`關鍵字](../cpp/auto-keyword.md)
