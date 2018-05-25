---
title: _control87、_controlfp、__control87_2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _control87
- _controlfp
- __control87_2
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48d0c3107bf2edc09017ea138e4c8024ce328dd8
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="control87-controlfp-control872"></a>_control87、_controlfp、__control87_2

取得和設定浮點控制字組。 更安全的版本 **_controlfp**便無法使用，請參閱[_controlfp_s](controlfp-s.md)。

## <a name="syntax"></a>語法

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>參數

*new*<br/>
新的控制字組位元值。

*遮罩*<br/>
要設定之新控制字組位元的遮罩。

*x86_cw*<br/>
填入 x87 浮點單位的控制字組。 傳遞 0 (**NULL**) 若要設定只 SSE2 控制字組。

*sse2_cw*<br/>
SSE 浮點單位的控制字組。 傳遞 0 (**NULL**) 若要設定只會將 x87 控制 word。

## <a name="return-value"></a>傳回值

如 **_control87**和 **_controlfp**中值, 的位元傳回表示浮點控制狀態。 如需所傳回的位元的完整定義 **_control87**，請參閱浮點數。H.

如 **__control87_2**，傳回的值為 1，以表示成功。

## <a name="remarks"></a>備註

**_Control87**函式取得和設定浮點控制字組。 浮點控制字組可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式 (視平台而定)。 您也可以使用 **_control87**要加上遮罩或取消遮罩的浮點例外狀況。 如果值*遮罩*等於 0， **_control87**取得浮點控制字組。 如果*遮罩*是控制字組的新值會設定為非零，： 位於任何位元 （也就是等於 1） 在*遮罩*中的對應位元*新*用來更新控制，word。 換句話說， **fpcntrl** = ((**fpcntrl** & ~*遮罩*) &#124; (*新* & *遮罩*))其中**fpcntrl**是浮點控制字組。

> [!NOTE]
> 根據預設，執行階段程式庫會遮罩所有浮點例外狀況。

**_controlfp**平台無關的可攜式版本 **_control87**。 它幾乎等同於 **_control87** x86、 x64 和 ARM 平台上的函式。 如果您的目標 x86、 x64 或 ARM 平台，使用 **_control87**或 **_controlfp**。

之間的差異 **_control87**和 **_controlfp**處於他們針對 DENORMAL 值的方式。 針對 x86、 x64 和 ARM 平台， **_control87**可以設定和清除異常運算元例外狀況遮罩。 **_controlfp**不會修改異常運算元例外狀況遮罩。 這個範例示範差異：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

可能的值遮罩常數 (*遮罩*) 和新控制項的值 (*新*) 會顯示在下表的十六進位值。 使用下面所列的可攜式常數 (**_MCW_EM**， **_EM_INVALID**，依此類推) 做為這些函式的引數，而不是提供十六進位值明確。

Intel x86 衍生平台支援 DENORMAL 輸入和輸出硬體中的值。 x86 行為是保留 DENORMAL 值。 ARM 平台和 x64 支援 SSE2 的平台可讓 DENORMAL 運算元和結果，以排清，或為零強制。 **_Controlfp**和 **_control87**函式提供的遮罩，若要變更此行為。 下列範例示範如何使用此遮罩。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台， **_control87**和 **_controlfp**函式套用到在 FPSCR 暫存器。 X64 架構，只 SSE2 控制字組儲存在 MXCSR 暫存器會受到影響。 在 x86 平台， **_control87**和 **_controlfp**影響控制項的文字將 x87 和 SSE2，如果有的話。 此函式 **__control87_2**啟用將 x87 和 SSE2 一起或分開控制浮點數的單位。 如果您想要影響這兩個單位，在以兩個整數的位址中傳遞**x86_cw**和**sse2_cw**。 如果您只想要影響的一個單位，地址中傳遞該參數，但傳遞 0 (**NULL**) 其他。 如果針對其中一個參數傳遞 0，則此函式不會影響該浮點單位。 如果程式碼的一部分使用 x87 浮點單位，而程式碼的另一個部分使用 SSE2 浮點單位，則此函式可能十分有用。 如果您使用 **__control87_2**一部分的其中一個程式和設定浮點控制字的不同值，然後使用 **_control87**或 **_controlfp**來進一步然後操作控制字組 **_control87**和 **_controlfp**可能無法傳回單一的控制字組，以代表兩個浮點數的單位的狀態。 在這種情況下，這些函式會將**EM_AMBIGUOUS**中傳回的整數值，表示兩個字與字之間不一致的旗標。 這警告所傳回的控制字組可能無法精確地呈現這兩個浮點控制字組的狀態。

在 ARM 和 x64 架構，變更無限大模式或浮點精確度不支援。 如果精確度控制遮罩適用於 x64 平台，此函數會引發判斷提示和無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

> [!NOTE]
> **__control87_2**不支援的 ARM 或 x64 架構。 如果您使用 **__control87_2**和您的程式編譯為 ARM 或 x64 架構，編譯器會產生錯誤。

當您使用時，這些函式會忽略[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯，因為 common language runtime (CLR) 只支援預設的浮點精確度。

**十六進位值**

如 **_MCW_EM**遮罩，清除遮罩設定允許的硬體例外狀況的例外狀況; 例外狀況會隱藏設定遮罩。 如果 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**就會發生下一步的浮點指令執行之前，會擲回任何硬體例外狀況。 若要產生的硬體例外狀況之後立即 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**，呼叫**FWAIT** MASM 指示。

|遮罩|十六進位值|常數|十六進位值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （異常控制項）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （插斷例外狀況遮罩）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （無限大控制）<br /><br /> (不支援 ARM 或 x64] 平台。)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （捨入控制項）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精確度控制）<br /><br /> （不支援在 ARM 或 x64 平台。）|0x00030000|**_PC_24** （24 位元）<br /><br /> **_PC_53** （53 位元）<br /><br /> **_PC_64** （64 位元）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_control87**， **_controlfp**， **_control87_2**|\<float.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cntrl87.c
// processor: x86
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87;

    // Show original x87 control word and do calculation.
    control_word_x87 = __control87_2(0, 0,
                                     &control_word_x87, 0);
    printf( "Original: 0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    control_word_x87 = __control87_2(_PC_24, MCW_PC,
                                     &control_word_x87, 0);
    printf( "24-bit:   0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,
                                     &control_word_x87, 0 );
    printf( "Default:  0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0001
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0x0001
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x0001
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
