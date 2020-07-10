---
title: intrinsic pragma
description: MSVC 內建 pragma 是用來指定支援的內建函式以當做內建函式使用。
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 31f4ebc2fdd4c5c984160d441b4e0a723c686a46
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180951"
---
# <a name="intrinsic-pragma"></a>`intrinsic` pragma

指定 pragma 引數清單中指定的函式呼叫為內建 (Intrinsic)。

## <a name="syntax"></a>語法

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>備註

**`intrinsic`** Pragma 會告訴編譯器函式有已知的行為。 如果會產生較佳的效能，則編譯器可能會呼叫函式，而不會以內嵌指令取代函式呼叫。

內建形式的程式庫函式如下所列。 一旦 **`intrinsic`** 看到 pragma，它就會在包含指定內建函式的第一個函式定義中生效。 效果會繼續到來源檔案的結尾，或 `function` 指定相同內建函式的 pragma 外觀。 **`intrinsic`** Pragma 只能用在全域層級的函式定義外部。

下列函式具有內建形式，而且當您指定時，會使用內建表單 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) ：

|  |  |  |  |
|--|--|--|--|
| [`_disable`](../intrinsics/disable.md) | [`_outp`](../c-runtime-library/outp-outpw-outpd.md) | [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md) | [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) |
| [`_enable`](../intrinsics/enable.md) | [`_outpw`](../c-runtime-library/outp-outpw-outpd.md) | [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) |
| [`_inp`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md) | [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) |
| [`_inpw`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) |  |
| [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md) | [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) | [`memset`](../c-runtime-library/reference/memset-wmemset.md) |  |
| [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md) | [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md) |  |

使用內建函式的程式速度較快，因為它們不會有函式呼叫的額外負荷。 不過，它們可能會因為產生額外的程式碼而變大。

### <a name="x86-specific-example"></a>x86 特定範例

和內建 `_disable` `_enable` 會產生核心模式指示，以停用或啟用中斷，而且在核心模式驅動程式中很有用。

從命令列編譯下列程式碼 `cl -c -FAs sample.c` ，並查看 *`sample.asm`* 以瞭解它們是否轉換成 X86 指示 CLI 和 STI：

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

### <a name="intrinsic-floating-point-functions"></a>內建函式浮點函式

這些浮點函數沒有真正的內部形式。 相反地，它們有版本直接將引數傳遞至浮點晶片，而不是在堆疊上推送：

|  |  |  |  |
|--|--|--|--|
| [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md) | [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md) | [`pow`](../c-runtime-library/reference/pow-powf-powl.md) | [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md) |
| [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md) | [`fmod`](../c-runtime-library/reference/fmod-fmodf.md) | [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md) |  |

當您指定 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) 和 [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (或任何包含 **`/Oi`** ： [`/Ox`](../build/reference/ox-full-optimization.md) 、 [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) 和) 的選項時，這些浮點函式具有真正的內部形式 [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ：

|  |  |  |  |
|--|--|--|--|
| [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`exp`](../c-runtime-library/reference/exp-expf.md) | [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md) |
| [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md) | [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md) |
| [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md) |  |  |  |

您可以使用 [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) 或 [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 來覆寫真正內建浮點選項的產生。 在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。

[`#pragma function`](../preprocessor/function-c-cpp.md)如需有關如何啟用和停用來源文字區塊之內建函式的詳細資訊和範例，請參閱。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 `__pragma` 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
