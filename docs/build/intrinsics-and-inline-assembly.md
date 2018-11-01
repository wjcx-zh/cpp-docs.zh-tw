---
title: 內建和內嵌組譯
ms.date: 11/04/2016
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
ms.openlocfilehash: 033225259c0a33414fe45eba313bb1f1c94eb379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515098"
---
# <a name="intrinsics-and-inline-assembly"></a>內建和內嵌組譯

其中一個條件約束，適用於 x64 編譯器會為沒有內嵌組譯工具支援。 函式，這表示無法寫入 C 或 c + + 中是必須可寫入為副程式或編譯器所支援的內建函式。 某些函式是效能敏感，而有些則不。 重視效能的函式應該實作為內建函式。

編譯器所支援的內建函式中所述[編譯器內建](../intrinsics/compiler-intrinsics.md)。

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)