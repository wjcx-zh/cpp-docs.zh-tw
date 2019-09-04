---
title: _control87、_controlfp、__control87_2
ms.date: 08/29/2019
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
ms.openlocfilehash: 75b2870543ec3ddd20d445a492ad4270b91e80d7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218425"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87、_controlfp、__control87_2

取得和設定浮點控制字組。 有更安全的 **_controlfp**版本可供使用;請參閱[_controlfp_s](controlfp-s.md)。

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

*new*\
新的控制字組位元值。

*遮罩*\
要設定之新控制字組位元的遮罩。

*x86_cw*\
填入 x87 浮點單位的控制字組。 傳入 0 (**Null**), 只設定 SSE2 控制字組。

*sse2_cw*\
SSE 浮點單位的控制字組。 傳入 0 (**Null**), 只設定 x87 控制字組。

## <a name="return-value"></a>傳回值

針對 **_control87**和 **_controlfp**, 傳回值中的位表示浮點控制狀態。 如需 **_control87**所傳回之位的完整定義, 請參閱 FLOAT。H.

若為 **__control87_2**, 則傳回值為 1, 表示成功。

## <a name="remarks"></a>備註

**_Control87**函數會取得和設定浮點控制字組。 浮點控制字組可讓程式變更精確度、四捨五入和無限大模式 (視平臺而定)。 您也可以使用 **_control87**來遮罩或取消遮罩浮點例外狀況。 如果*mask*的值等於 0, **_control87**會取得浮點控制字組。 如果*mask*不是零, 則會設定控制字組的新值:若是在*mask*中的任何位 (即等於 1), 則會使用*new*中的對應位來更新控制字組。 換句話說, **fpcntrl** = ((**fpcntrl** & ~*mask*) &#124; (*新* & 的*mask*)), 其中**fpcntrl**是浮點控制字組。

> [!NOTE]
> 根據預設，執行階段程式庫會遮罩所有浮點例外狀況。

**_controlfp**是與平臺無關、可移植的 **_control87**版本, 幾乎與 **_control87**函式完全相同。 如果您的程式碼是以多個平臺為目標, 請使用 **_controlfp**或 **_controlfp_s**。 **_Control87**和 **_controlfp**之間的差異在於它們處理 DENORMAL 值的方式。 針對 x86、x64、ARM 和 ARM64 平臺, **_control87**可以設定並清除 DENORMAL 運算元例外狀況遮罩。 **_controlfp**不會修改 DENORMAL 運算元例外狀況遮罩。 這個範例示範差異：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Mask 常數 (*mask*) 和新控制項值 (*new*) 的可能值會顯示在 [控制文字遮罩] 和 [值] 資料表中。 使用下面所列的可移植常數 ( **_MCW_EM**、 **_EM_INVALID**等) 作為這些函式的引數, 而不是明確地提供十六進位值。

Intel x86 衍生平臺支援硬體中的 DENORMAL 輸入和輸出值。 x86 行為是保留 DENORMAL 值。 ARM 和 ARM64 平臺以及具有 SSE2 支援的 x64 平臺可讓 DENORMAL 運算元和結果排清, 或強制為零。 **_Controlfp**和 **_control87**函數會提供遮罩來變更此行為。 下列範例示範如何使用此遮罩。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 和 ARM64 平臺上, **_control87**和 **_controlfp**函式適用于 fpscr 暫存器暫存器。 只有儲存在 MXCSR 暫存器中的 SSE2 控制項字會受到 x64 平臺的影響。 在 x86 平臺上, **_control87**和 **_controlfp**會影響 x87 和 SSE2 (如果有的話) 的控制字組。

函式 **__control87_2**可讓 X87 和 SSE2 浮點單位一起或分開控制。 若要影響這兩個單位, 請將兩個整數的位址傳入**x86_cw**和**sse2_cw**。 如果您只想要影響一個單位, 請傳入該參數的位址, 但為另一個傳入 0 (**Null**)。 如果針對其中一個參數傳遞 0，則此函式不會影響該浮點單位。 當程式碼的一部分使用 x87 浮點單位, 而且另一個部分使用 SSE2 浮點單位時, 這會很有用。

如果您使用 **__control87_2**為浮點控制字組設定不同的值, 則 **_control87**或 **_controlfp**可能無法傳回單一控制項單字來表示這兩個浮點單位的狀態。 在這種情況下, 這些函式會在傳回的整數值中設定**EM_AMBIGUOUS**旗標, 以指出兩個控制字組之間的不一致。 **EM_AMBIGUOUS**旗標是一項警告, 表示傳回的控制字組可能不會正確地代表這兩個浮點控制字組的狀態。

在 ARM、ARM64 和 x64 平臺上, 不支援變更無限大模式或浮點精確度。 如果在 x64 平臺上使用精確度控制遮罩, 則函式會引發判斷提示, 並叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

> [!NOTE]
> ARM、ARM64 或 x64 平臺不支援 **__control87_2** 。 如果您使用 **__control87_2** , 並針對 ARM、ARM64 或 x64 平臺編譯您的程式, 編譯器會產生錯誤。

當您使用[/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時, 會忽略這些函數。 Common language runtime (CLR) 只支援預設的浮點精確度。

### <a name="control-word-masks-and-values"></a>控制文字遮罩和值

針對 **_MCW_EM** mask, 清除遮罩會設定例外狀況, 以允許硬體例外狀況;設定遮罩會隱藏例外狀況。 如果發生 **_EM_UNDERFLOW**或 **_EM_OVERFLOW** , 則在執行下一個浮點指令之前, 不會擲回任何硬體例外狀況。 若要在 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**之後立即產生硬體例外狀況, 請呼叫**FWAIT** MASM 指令。

|遮罩|十六進位值|常數|十六進位值|
|----------|---------------|--------------|---------------|
|**_MCW_DN**(Denormal 控制項)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM**(中斷例外狀況遮罩)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC**(無限大控制項)<br /><br /> (在 ARM 或 x64 平臺上不支援)。|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC**(進位控制項)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC**(精確度控制)<br /><br /> (在 ARM 或 x64 平臺上不支援)。|0x00030000|**_PC_24**(24 位)<br /><br /> **_PC_53**(53 位)<br /><br /> **_PC_64**(64 位)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_control87**、 **_controlfp**、 **_control87_2**|\<float.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)\
[_clear87、_clearfp](clear87-clearfp.md)\
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
