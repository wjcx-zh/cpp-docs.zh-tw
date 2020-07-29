---
title: 編譯器警告 (層級 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: b17df9d7a9997e5d8ef37a4721de8693968cbbdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214447"
---
# <a name="compiler-warning-level-1-c4910"></a>編譯器警告 (層級 1) C4910

' \<identifier> '： ' __declspec （dllexport） ' 和 ' extern ' 在明確具現化上不相容

名為的明確樣板具 *\<identifier>* 現化是由 `__declspec(dllexport)` 和 **`extern`** 關鍵字所修改。 不過，這些關鍵字是互斥的。 `__declspec(dllexport)`關鍵字表示具現化樣板類別，而 **`extern`** 關鍵字則表示不會自動具現化範本類別。

## <a name="see-also"></a>另請參閱

[明確具現化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般規則和限制](../../cpp/general-rules-and-limitations.md)
