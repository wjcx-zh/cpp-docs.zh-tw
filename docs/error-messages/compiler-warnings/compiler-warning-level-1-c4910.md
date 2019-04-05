---
title: 編譯器警告 (層級 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 49cbbf3369fc4765d93e67e2dca84a4d975560d7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027538"
---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910

'\<識別項 >': '__declspec （dllexport）' 和 'extern' 在明確具現化不相容

名為明確樣板具現化*\<識別項 >* 所修改之`__declspec(dllexport)`和`extern`關鍵字。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。

## <a name="see-also"></a>另請參閱

[明確初始化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般規則和限制](../../cpp/general-rules-and-limitations.md)