---
title: fp_contract | Microsoft Docs
ms.custom: 
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28c9b6287b71e077a7d91c60d2062b9f7243d103
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="fpcontract"></a>fp_contract

判斷是否已發生浮點縮減。 浮點縮減是例如 FMA （Fused 乘以-新增），它結合了兩個個別浮點運算到單一指令的指示。 使用這些指示會影響浮點數的精確度，因為而不是捨入每個作業之後，處理器可能會捨入一次這兩項作業之後。

## <a name="syntax"></a>語法

> **#pragma fp_contract (** { **on** | **off** } **)**  

## <a name="remarks"></a>備註  

根據預設， **fp_contract**是**上**。 這會告訴編譯器將儘可能使用浮點縮減指示。 設定**fp_contract**至**關閉**以保留個別浮點指示。

如需有關浮點數行為的詳細資訊，請參閱[/fp （指定浮點行為）](../build/reference/fp-specify-floating-point-behavior.md)。

其他浮點 pragma 包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>範例

這個範例產生的程式碼不使用--融合的指示，即使它使用目標處理器上。 如果您註解`#pragma fp_contract (off)`，產生的程式碼可能會使用--融合指令，如果有的話。  
  
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

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
