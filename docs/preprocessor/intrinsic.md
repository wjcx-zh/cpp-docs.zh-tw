---
title: 內建函式 |Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs:
- C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af7fe3a96a31f636a0a1c45b1ee74dd4006d15fe
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071595"
---
# <a name="intrinsic"></a>intrinsic

指定 pragma 引數清單中指定的函式呼叫為內建 (Intrinsic)。

## <a name="syntax"></a>語法

```cpp
#pragma intrinsic( function1 [, function2, ...] )
```

## <a name="remarks"></a>備註

**內建**pragma 會告知編譯器函式具有已知行為。  如果會產生較佳的效能，則編譯器可能會呼叫函式，而不會以內嵌指令取代函式呼叫。

內建形式的程式庫函式如下所列。 一次**內建**pragma，它會在包含指定的內建函式的第一個函式定義的生效。 其作用會持續到原始程式檔的結尾，或是的外觀`function`pragma 指定相同的內建函式。 **內建**pragma 可以用只在函式定義之外，在全域層級。

下列函式具有內建函式的形式和您指定時，會使用內建形式[/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

使用內建函式的程式速度較快，因為它們不需額外負擔函式呼叫，但是也因為會產生額外的程式碼，所以體積比較大。

**x86 特定**

`_disable`和`_enable`內建函式會產生核心模式指示停用/啟用中斷，而且可能會用於核心模式驅動程式。

### <a name="example"></a>範例

從命令列使用下列程式碼編譯`cl -c -FAs sample.c`並查看 sample.asm，這些指令變成 x86 指令 CLI 和 STI:

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

**X86 專屬資訊結束**

下列浮點函式沒有真正的內建形式。 它們是使用版本直接將引數傳遞至浮點晶片，而不是將引數推送至程式堆疊：

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

下列浮點函式具有 true 的內建形式，當您指定[/Oi](../build/reference/oi-generate-intrinsic-functions.md)， [/Og](../build/reference/og-global-optimizations.md)，並[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md) (或任何選項，其中包含 /Og: [/Ox](../build/reference/ox-full-optimization.md)， [/o1](../build/reference/o1-o2-minimize-size-maximize-speed.md)，和/o2):

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

您可以使用[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)或是[/Za](../build/reference/za-ze-disable-language-extensions.md)覆寫產生真正的內建浮點選項。 在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。

請參閱[#pragma 函式](../preprocessor/function-c-cpp.md)資訊及如何啟用/停用內建函式的原始程式文字區塊的範例。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)