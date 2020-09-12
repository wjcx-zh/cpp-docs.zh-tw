---
title: float_control pragma
description: 描述 float_control pragma 指示詞的使用方式和效果。 Float_control 指示詞會在執行時間控制浮點精確語義和例外狀況語義的狀態。
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 02a8e8d80616623693fff04aca02355c505b4c3b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041922"
---
# <a name="float_control-pragma"></a>float_control pragma

指定函式的浮點行為。

## <a name="syntax"></a>語法

> **#pragma float_control**\
> **#pragma float_control ( 精確、** { **on**  |  **off** } [ **、push** ] **) **\
> **#pragma float_control ( 例外，** { **on**  |  **off** } [ **，push** ] **) **\
> **#pragma float_control (** { **push**  |  **pop** } **) **

## <a name="options"></a>選項

**精確**、 **on**  |  **關閉**、**推**播\
指定是否要 **啟用) 的** (，或停用 (**off**) 精確的浮點語義。 如需有關與 **/fp：精確** 編譯器選項之差異的詳細資訊，請參閱「備註」一節。 選擇性的**推**播 token 會將 float_control 的目前設定推送至內部編譯器堆疊上的**float_control** 。

**except**、 **on**  |  ** **、 **push**\
指定是否要啟用) 的 (，**或停用) 浮點**例外狀況**語義的 (** 。 選擇性的**推**播 token 會將 float_control 的目前設定推送至內部編譯器堆疊上的**float_control** 。

**只有當****精確**的也設為**on**時，才能設定為**on** 。

**推**\
將目前的 **float_control** 設定推入至內部編譯器堆疊。

**流行**\
從內部編譯器堆疊的頂端移除 **float_control** 設定，並使新的 **float_control** 設定。

## <a name="remarks"></a>備註

**Float_control** pragma 與[/fp](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項的行為不同。 **Float_control** pragma 只會控制浮點行為的一部分。 它必須與 [fp_contract](../preprocessor/fp-contract.md) 和 [fenv_access](../preprocessor/fenv-access.md) pragma 結合，才能重新建立 **/fp** 編譯器選項。 下表顯示每個編譯器選項的對等 pragma 設定：

| 選項 | float_control (精確、 \*)  | float_control (除了、 \*)  | fp_contract (\*)  | fenv_access (\*)  |
|-|-|-|-|-|
| /fp： strict             | on  | on  | 關 | on  |
| /fp：精確            | on  | 關 | on  | 關 |
| /fp： fast               | 關 | 關 | on  | 關 |

換句話說，您可能需要使用數個 pragma 組合來模擬 **/fp： fast**、 **/fp：精確**和 **/fp： strict** 命令列選項。

您可以使用 **float_control** 和 **fenv_access** 浮點數 pragma 組合的方式有一些限制：

- 如果已啟用精確的**語法，您**只能使用**float_control**設定為**on** 。 您可以使用 **float_control** pragma 或 **/fp：精確** 或 **/fp： strict** 編譯器選項來啟用精確的語義。

- 啟用例外狀況的語法時，您不能使用 **float_control** 來關閉 **精確** 的，無論是透過 **float_control** pragma 或 **/fp： except** 編譯器選項。

- 除非透過**float_control** pragma 或編譯器選項啟用精確的語義，否則您無法啟用**fenv_access** 。

- 啟用**fenv_access**時，您無法使用**float_control**來關閉**精確度**。

這些限制表示某些浮點 pragma 的順序很重要。 若要使用 pragma 從 fast 模型移至 strict 模型，請使用下列程式碼：

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

若要使用 **float_control** pragma 從 strict 模型移至快速模型，請使用下列程式碼：

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

如果未指定任何選項， **float_control** 不會有任何作用。

## <a name="example"></a>範例

下列範例顯示如何使用 pragma **float_control**攔截溢位浮點例外狀況。

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
