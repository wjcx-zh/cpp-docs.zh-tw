---
title: intrinsic pragma
description: MSVC 內建 pragma 可用來指定要當做內建函式使用的支援內建函式。
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 45a5a13f3bda3657b93e1a89e7a842a4465b01d5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041103"
---
# <a name="intrinsic-pragma"></a>`intrinsic` pragma

指定 pragma 引數清單中指定的函式呼叫為內建 (Intrinsic)。

## <a name="syntax"></a>語法

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>備註

**`intrinsic`** Pragma 會告知編譯器函數有已知的行為。 如果會產生較佳的效能，則編譯器可能會呼叫函式，而不會以內嵌指令取代函式呼叫。

內建形式的程式庫函式如下所列。 一旦 **`intrinsic`** 出現 pragma 之後，它就會在包含指定內建函式的第一個函式定義上生效。 效果會持續到原始程式檔的結尾，或是 `function` 指定相同內建函式的 pragma 外觀。 **`intrinsic`** Pragma 只能用在全域層級的函式定義外部。

下列函式具有內建表單，當您指定時，會使用內建表單 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) ：

:::row:::
   :::column span="":::
      [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_disable`](../intrinsics/disable.md)\
      [`_enable`](../intrinsics/enable.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_inp`](../c-runtime-library/inp-inpw-inpd.md)\
      [`_inpw`](../c-runtime-library/inp-inpw-inpd.md)\
   :::column-end:::
   :::column span="":::
      [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md)\
      [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md)\
   :::column-end:::
   :::column span="":::
      [`memset`](../c-runtime-library/reference/memset-wmemset.md)\
      [`_outp`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_outpw`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
      [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
   :::column-end:::
   :::column span="":::
      [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md)\
      [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)\
      [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)\
      [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
      [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)\
   :::column-end:::
:::row-end:::

使用內建函式的程式較快，因為它們沒有函式呼叫的額外負荷。 不過，它們可能會因為產生額外的程式碼而變得較大。

### <a name="x86-specific-example"></a>x86 特定範例

`_disable`和 `_enable` 內建函式會產生核心模式的指示，以停用或啟用中斷，而且在核心模式驅動程式中可能很有用。

從命令列編譯下列 `cl -c -FAs sample.c` 程式碼，並查看它們是否 *`sample.asm`* 變成 X86 指示 CLI 和 STI：

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

### <a name="intrinsic-floating-point-functions"></a>內建浮點函數

這些浮點函數沒有真正的內部形式。 相反地，它們具有將引數直接傳遞至浮點晶片的版本，而不是在堆疊上推送引數：

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
   :::column-end:::
   :::column span="":::
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
   :::column-end:::
   :::column span="":::
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
   :::column-end:::
   :::column span="":::
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)\
   :::column-end:::
:::row-end:::

當您指定 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) 和 [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (或包含 **`/Oi`** ： [`/Ox`](../build/reference/ox-full-optimization.md) 、 [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) 和) 的任何選項時，這些浮點數函式具有真正的內建形式 [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ：

:::row:::
   :::column span="":::
      [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
   :::column-end:::
   :::column span="":::
      [`exp`](../c-runtime-library/reference/exp-expf.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
   :::column-end:::
   :::column span="":::
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
   :::column-end:::
   :::column span="":::
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
   :::column-end:::
:::row-end:::

您可以使用 [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) 或覆 [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 寫產生 true 內建函式的浮點選項。 在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。

如需 [`#pragma function`](../preprocessor/function-c-cpp.md) 有關如何啟用及停用來源文字區塊之內建函式的詳細資訊和範例，請參閱。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 `__pragma` 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
