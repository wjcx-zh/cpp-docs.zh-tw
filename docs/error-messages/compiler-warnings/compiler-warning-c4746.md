---
title: 編譯器警告 C4746
ms.date: 11/04/2016
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 1b79eed2134b8c6310e508e56b3388c6f38fe4b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625884"
---
# <a name="compiler-warning-c4746"></a>編譯器警告 C4746

暫時性存取的 '\<運算式 >' 受限於 /volatile: [iso&#124;ms] 設定，請考慮使用 __iso_volatile_load/store 內建函式。

每當 volatile 變數直接存取時就會發出 C4746。 它要協助開發人員識別受目前指定的特定暫時性模型的程式碼位置 (這可以透過控制[/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項)。 特別是，當使用 /volatile:ms 時，有助於尋找編譯器產生的硬體記憶體屏障。

__iso_volatile_load/store 內建可用來明確存取揮發性記憶體，而不受暫時性模型影響。 使用這些內建函式不會觸發 C4746。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。