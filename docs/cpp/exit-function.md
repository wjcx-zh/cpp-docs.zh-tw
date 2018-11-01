---
title: exit 函式
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
ms.openlocfilehash: 82c9d00a49c8a080d893a51052739a0265ad0860
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532557"
---
# <a name="exit-function"></a>exit 函式

**結束**函式，在標準 include 檔中宣告\<stdlib.h >，會終止 c + + 程式。

提供做為引數的值**結束**會傳回到作業系統與程式的傳回碼或結束程式碼。 依照慣例，傳回碼為零，表示程式順利完成。

> [!NOTE]
>  您可以使用 EXIT_FAILURE 和 EXIT_SUCCESS、 中定義的常數\<stdlib.h >，以指出成功或失敗的程式。

發出**會傳回**陳述式，從`main`函式相當於呼叫**結束**函式傳回的值作為其引數。

如需詳細資訊，請參閱 <<c0> [ 結束](../c-runtime-library/reference/exit-exit-exit.md)中*執行階段程式庫參考*。

## <a name="see-also"></a>另請參閱

[程式終止](../cpp/program-termination.md)