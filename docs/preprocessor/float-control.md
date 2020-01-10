---
title: float_control pragma
description: 描述 float_control pragma 指示詞的用法和效果。 Float_control 指示詞會在執行時間控制浮點精確的語義和例外狀況語義的狀態。
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 0c9caea5ba35a55a53f7b9340cf9bfd2cce80561
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305497"
---
# <a name="float_control-pragma"></a>float_control pragma

指定函式的浮點行為。

## <a name="syntax"></a>語法

> **#pragma float_control**\
> **#pragma float_control （精確，** { **on** | **off** } [ **，push** ] **）** \
> **#pragma float_control （除外，** { **on** | **off** } [ **，push** ] **）** \
> **#pragma float_control （** { **push** | **pop** } **）**

## <a name="options"></a>選項

**精確**、**在** | **off**、 **push**\
指定是否啟用（**開啟**）或停用（**關閉**）精確的浮點語義。 如需此選項與類似名稱的 **/fp：精確**編譯器選項有何差異的詳細資訊，請參閱備註一節。 選擇性的**推送**權杖會指示編譯器在內部編譯器堆疊上推送**float_control**的目前設定。

**除了**，**在** | **關閉** 上，**推送**\
指定是否啟用（**開啟**）或停用（**關閉**）浮點例外狀況的語義。 如需此選項與類似名稱為 **/fp： except**編譯器選項之差異的詳細資訊，請參閱備註一節。 選擇性的**推送**權杖會指示編譯器在內部編譯器堆疊上推送**float_control**的目前設定。

**除了**[**精確**] 也設定為 [**開啟**] 時，[只能] 設定為 [**開啟**]。

**推送**\
將目前的**float_control**設定推送至內部編譯器堆疊。

**pop**\
從內部編譯器堆疊頂端移除**float_control**設定，並讓新的**float_control**設定。

## <a name="remarks"></a>備註

[**精確**] 和 [**除外**] 選項的行為與相同名稱的[/fp](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項並沒有完全相同。 **Float_control** pragma 只會控制浮點行為的一部分。 它必須與[fp_contract](../preprocessor/fp-contract.md)和[fenv_access](../preprocessor/fenv-access.md) pragma 結合，才能重新建立 **/fp**編譯器選項。 下表顯示每個編譯器選項的對等 pragma 設定：

| | float_control （精確，\*） | float_control （除外，\*） | fp_contract （\*） | fenv_access （\*） |
|-|-|-|-|-|
| /fp： strict             | 於  | 於  | 停止 | 於  |
| /fp： strict/fp： except- | 於  | 停止 | 停止 | 於  |
| /fp：精確            | 於  | 停止 | 於  | 停止 |
| /fp：精確/fp： except | 於  | 於  | 於  | 停止 |
| /fp： fast               | 停止 | 停止 | 於  | 停止 |

換句話說，您必須使用數個 pragma 來模擬 **/fp： fast**、 **/fp：精確**、 **/fp： strict**和 **/fp： except**命令列選項。

您可以使用**float_control**和**fenv_access**浮點 pragma 的方式有一些限制：

- 只有在已啟用精確的語義時，才可以使用**float_control**來設定 on**以外** **的**。 您可以透過**float_control** pragma 或使用 **/fp：精確**或 **/fp： strict**編譯器選項來啟用精確的語義。

- 當例外狀況的語義啟用時，您無法使用**float_control**來進行**精確**關閉，不論是由**float_control** pragma 或 **/fp： except**編譯器選項。

- 除非啟用了精確的語義，否則您無法啟用**fenv_access** ，不論是透過**float_control** pragma 或編譯器選項。

- 啟用**fenv_access**時，您無法使用**float_control**來關閉**精確**的功能。

這些限制表示某些浮點 pragma 的順序很重要。 若要使用**float_control**和相關的 pragma 從快速模型移至 strict 模型，請使用下列程式碼：

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

若要使用**float_control** pragma 從 strict 模型移至快速模型，請使用下列程式碼：

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // ensable contractions
```

如果未指定任何選項， **float_control**不會有任何作用。

## <a name="example"></a>範例

下列範例顯示如何使用 pragma **float_control**攔截溢位的浮點例外狀況。

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
