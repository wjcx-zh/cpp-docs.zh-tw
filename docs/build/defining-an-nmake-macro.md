---
title: 定義 NMAKE 巨集
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 860a5766e0d766f7426cb6c1a7eaf5db02686aa4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498968"
---
# <a name="defining-an-nmake-macro"></a>定義 NMAKE 巨集

## <a name="syntax"></a>語法

```

macroname=string
```

## <a name="remarks"></a>備註

*Macroname*結合字母、 數字和底線 (_) 最多 1,024 個字元，且大小寫區分大小。 *Macroname*可以包含已叫用的巨集。 如果*macroname*包含完全是叫用的巨集，所叫用巨集不得為 null 或未定義。

`string`可以是任何零或多個字元序列。 Null 字串，包含零個字元或只有空格或定位字元。 `string`可以包含的巨集引動過程。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[在巨集中的特殊字元](../build/special-characters-in-macros.md)

[Null 和未定義的巨集](../build/null-and-undefined-macros.md)

[定義巨集的位置](../build/where-to-define-macros.md)

[巨集定義的優先順序](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>另請參閱

[巨集和 NMAKE](../build/macros-and-nmake.md)