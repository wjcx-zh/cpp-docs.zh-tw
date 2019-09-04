---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219764"
---
# <a name="__ud2"></a>__ud2

**Microsoft 專屬**

產生未定義的指令。

## <a name="syntax"></a>語法

```C
void __ud2();
```

## <a name="remarks"></a>備註

如果您執行未定義的指令, 處理器會引發不正確 opcode 例外狀況。

函式相當`UD2`于機器指令, 而且只能在核心模式中使用。 `__ud2` 如需詳細資訊, 請搜尋檔「Intel 架構軟體發展人員手冊, 第2卷:指示集參考, 位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ud2`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="example"></a>範例

下列範例會執行未定義的指令, 這會引發例外狀況。 然後, 例外狀況處理常式會將傳回碼從零變更為一。

```cpp
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
