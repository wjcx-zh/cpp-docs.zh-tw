---
title: _control87、_controlfp、__control87_2
ms.date: 04/05/2018
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
ms.openlocfilehash: e2ebfdc80a451ebf02563f78a62dd08618f92bcd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340413"
---
# <a name="control87-controlfp-control872"></a>_control87、_controlfp、__control87_2

取得和設定浮點控制字組。 更安全的版本 **_controlfp**可用; 請參閱[_controlfp_s](controlfp-s.md)。

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

*mask*<br/>
要設定之新控制字組位元的遮罩。

*x86_cw*<br/>
填入 x87 浮點單位的控制字組。 傳入 0 (**NULL**) 若要設定只 SSE2 控制字組。

*sse2_cw*<br/>
SSE 浮點單位的控制字組。 傳入 0 (**NULL**) 來僅設定 x87 控制字組。

## <a name="return-value"></a>傳回值

針對 **_control87**並 **_controlfp**，在值中的位元會傳回表示浮點控制狀態。 如需完整的定義所傳回的位元 **_control87**，請參閱浮點數。H.

針對 **__control87_2**，傳回的值是 1，表示成功。

## <a name="remarks"></a>備註

**_Control87**函式取得和設定浮點控制字組。 浮點控制字組可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式 (視平台而定)。 您也可以使用 **_control87**來遮罩或取消遮罩浮點例外狀況。 如果值*遮罩*等於 0， **_control87**取得浮點控制字組。 如果*遮罩*是設定組的非零值，控制字組的新值是：任何位元，是在 （也就是等於 1） 中*遮罩*中的對應位元*新*用來更新控制字組。 亦即**fpcntrl** = ((**fpcntrl** & ~*遮罩*) &#124; (*新* & *遮罩*))何處**fpcntrl**是浮點控制字組。

> [!NOTE]
> 根據預設，執行階段程式庫會遮罩所有浮點例外狀況。

**_controlfp**平台無關的可攜式版本 **_control87**。 它幾乎等同於 **_control87** x86、 x64 和 ARM 平台上的函式。 如果您的目標 x86、 x64 或 ARM 平台，使用 **_control87**或是 **_controlfp**。

之間的差異 **_control87**並 **_controlfp**在於它們如何處理 DENORMAL 值。 適用於 x86、 x64 和 ARM 平台， **_control87**可以設定和清除 DENORMAL OPERAND 例外狀況遮罩。 **_controlfp**不會修改 DENORMAL OPERAND 例外狀況遮罩。 這個範例示範差異：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

可能的值遮罩常數 (*遮罩*) 和新的控制項值 (*新*) 下的十六進位值表所示。 使用下面所列的可攜式常數 (**_MCW_EM**， **_EM_INVALID**等等) 作為這些函式的引數，而不是提供十六進位值明確。

Intel x86 衍生的平台支援的 DENORMAL 輸入和輸出在硬體中的值。 x86 行為是保留 DENORMAL 值。 在 ARM 平台和 x64 支援 SSE2 的平台可讓 DENORMAL 運算元和結果，以排清，或強制為零。 **_Controlfp**並 **_control87**函式提供遮罩來變更此行為。 下列範例示範如何使用此遮罩。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台， **_control87**並 **_controlfp**函式套用至 FPSCR 暫存器。 在 x64 架構，只將 SSE2 控制字組儲存在 MXCSR 暫存器會受到影響。 在 x86 平台 **_control87**並 **_controlfp**會影響 x87 和 SSE2，控制字組，如果有的話。 此函式 **__control87_2** x87 和 SSE2 浮點單位一起或分開控制會啟用。 如果您想要影響這兩個單位，在兩個整數的位址中傳遞**x86_cw**並**sse2_cw**。 如果您只想要影響一個單位，為該參數傳入的位址，但傳入 0 (**NULL**) 為其他。 如果針對其中一個參數傳遞 0，則此函式不會影響該浮點單位。 如果程式碼的一部分使用 x87 浮點單位，而程式碼的另一個部分使用 SSE2 浮點單位，則此函式可能十分有用。 如果您使用 **__control87_2**程式的某個部分和設定浮點控制字組不同的值，然後使用 **_control87**或是 **_controlfp**進一步操作控制字組，然後 **_control87**並 **_controlfp**可能無法傳回單一控制字組來代表這兩個浮點單位的狀態。 在此情況下，這些函式會將**則 EM_AMBIGUOUS**中傳回的整數值，指出兩個控制字組之間不一致的旗標。 這警告所傳回的控制字組可能無法精確地呈現這兩個浮點控制字組的狀態。

在 ARM 和 x64 上不支援變更無效模式或浮點精確度的架構。 如果精確度控制遮罩可在 x64 平台，此函式會引發判斷提示和無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。

> [!NOTE]
> **__control87_2**不支援 ARM 或 x64 架構。 如果您使用 **__control87_2**及編譯您的程式，針對 ARM 或 x64 架構，編譯器會產生錯誤。

當您使用時，會忽略這些函式[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯，因為 common language runtime (CLR) 只支援預設的浮點精確度。

**十六進位值**

針對 **_MCW_EM**遮罩，清除遮罩設定的例外狀況，以允許硬體例外狀況; 設定遮罩則會隱藏例外狀況。 如果 **_EM_UNDERFLOW**或是 **_EM_OVERFLOW**發生，直到執行下一個浮點指令，會擲回任何硬體例外狀況。 若要產生硬體例外狀況之後立即 **_EM_UNDERFLOW**或是 **_EM_OVERFLOW**，呼叫**FWAIT** MASM 指令。

|遮罩|十六進位值|常數|十六進位值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （異常控制項）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （插斷例外狀況遮罩）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （無限大控制項）<br /><br /> (不支援 ARM 或 x64] 平台。)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （四捨五入控制項）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精確度控制項）<br /><br /> （不支援 ARM 或 x64 平台。）|0x00030000|**_PC_24** （24 位元）<br /><br /> **_PC_53** （53 位元）<br /><br /> **_PC_64** （64 位元）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
