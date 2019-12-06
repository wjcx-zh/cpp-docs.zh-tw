---
title: 使用 wmain 取代 main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: f47d7219a54b197ec59f109cf08879774b48e6f7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857212"
---
# <a name="using-wmain-instead-of-main"></a>使用 wmain 取代 main

**Microsoft 專屬**

在 Unicode 程式設計模型中，您可以定義寬字元版本的 `main` 函數。 如果您想要撰寫符合 Unicode 規格的可移植程式碼，請使用**wmain** ，而不是 `main`。

您可以使用類似的格式 `main`，將正式參數宣告為**wmain** 。 然後您可以傳遞寬字元引數以及 (選擇性的) 一個指向程式的寬字元環境指標。 **Wmain**的*argv*和*envp*參數是 `wchar_t*`的類型。

如果您的程式使用 `main` 函式，則在程式啟動時，作業系統會建立多位元組字元環境。 只有在需要時（例如，藉由呼叫[_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)或[_wputenv](../c-runtime-library/reference/putenv-wputenv.md)函式），才會建立環境的寬字元複本。 在第一次呼叫 `_wputenv` 時，或在第一次呼叫 `_wgetenv` 時，如果 MBCS 環境已經存在，則會建立對應的寬字元字串環境，然後再由 `_wenviron` 全域變數 (是 `_environ` 全域變數的寬字元版本) 指向該變數。 此時會同時存在兩個環境 (MBCS 和 Unicode) 的複本，並由作業系統在整個程式存留期裡進行維護。

同樣地，如果您的程式使用**wmain**函式，則會在第一次呼叫 `_putenv` 或 `getenv`時建立 MBCS （ASCII）環境，並由 `_environ` 全域變數指向。

如需 MBCS 環境的詳細資訊，請參閱《*執行時間程式庫參考*》中的[單一位元組和多位元組字元集](../c-runtime-library/single-byte-and-multibyte-character-sets.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[main：程式啟動](../cpp/main-program-startup.md)