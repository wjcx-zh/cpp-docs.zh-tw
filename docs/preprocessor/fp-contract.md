---
title: fp_contract pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 833d8e7f4b8c9da18901610e52afed619468c5c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218558"
---
# <a name="fp_contract-pragma"></a>fp_contract pragma

判斷是否發生浮點縮減。 浮點縮減是將兩個不同的浮點運算結合成單一指令的一個指令, 例如 FMA (已融合的乘法-Add)。 使用這些指示可能會影響浮點精確度, 因為在這兩個作業之後, 處理器只能四捨五入一次。

## <a name="syntax"></a>語法

> **#pragma fp_contract (** { **on** | **off** } **)**

## <a name="remarks"></a>備註

根據預設, **fp_contract**是**on**。 這會告訴編譯器在可能的情況下使用浮點縮減指令。 將**fp_contract**設定為**off** , 以保留個別的浮點指示。

如需浮點行為的詳細資訊, 請參閱[/fp (指定浮點行為)](../build/reference/fp-specify-floating-point-behavior.md)。

其他浮點 pragma 包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>範例

從這個範例產生的程式碼並不會使用已融合的乘法-add 指示, 即使它在目標處理器上可用也一樣。 如果您將標記`#pragma fp_contract (off)`為批註, 則產生的程式碼可能會使用已融合的乘法-add 指示 (如果有的話)。

```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
