---
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 4b36cc9f5ed83b68cb15c39be91165ed7aa86d7b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348526"
---
# <a name="_controlfp_s"></a>_controlfp_s

取得和設定浮點控制字組。 這版的 [_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>參數

*電流控制*<br/>
目前的控制字組位元值。

*新控制*<br/>
新的控制字組位元值。

*遮罩*<br/>
要設定之新控制字組位元的遮罩。

## <a name="return-value"></a>傳回值

如果成功,則為零,或**錯誤**值錯誤代碼。

## <a name="remarks"></a>備註

**_controlfp_s**函數是**獨立於**平臺、更安全的_control87版本,它將浮點控制詞放入存儲在*當前控制*中的位址,並使用*newControl*進行設置。 值中的位元表示浮點控制狀態。 浮點控制狀態可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式 (視平台而定)。 您還可以使用 **_controlfp_s**來遮罩或取消掩碼浮點異常。

如果*遮罩*的數值等於 0,_controlfp_s取得 **_controlfp_s**浮點控制字並將檢索的值儲存在*目前的Control 中*。

如果*遮罩*是非零,則為控制項字設定新值:對於*蒙版*中設定的任何位(即等於 1),將使用*new*中的相應位更新控制項字。 換句話說 *,fpcntrl* = (fpcntrl & =*掩碼*) &#124; (*新控制* & *掩碼*) ), 其中*fpcntrl*是浮點控制詞。* * 在這種情況下,當前控制在更改完成後設置為值;因此,在更改完成後,將*當前控制*設置為該值。它不是舊的控制字位值。

> [!NOTE]
> 根據預設，執行階段程式庫會遮罩所有浮點例外狀況。

**_controlfp_s**與英特爾 (x86)、x64 和 ARM 平臺上**的_control87**功能幾乎相同。 如果目標是 x86、x64 或 ARM 平臺,則可以使用 **_control87**或 **_controlfp_s**。

**_control87**和 **_controlfp_s**之間的區別在於它們如何處理非正常值。 對於英特爾 (x86)、x64 和 ARM 平臺 **,_control87**可以設置和清除 DENORMAL OPERAND 異常遮罩。 **_controlfp_s**不會修改 DENORMAL OPERAND 異常遮罩。 這個範例示範差異：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

遮罩常數 (*遮罩*) 和新的控制項值 (*newControl*) 的可能值顯示在以下十六進位值表中。 使用下面列出的可移植常量 **(_MCW_EM、_EM_INVALID**等)作為這些函數的參數,而不是顯式提供十六進位值 **_EM_INVALID**。

Intel (x86) 衍生的平台支援硬體中的 DENORMAL 輸入和輸出值。 x86 行為是保留 DENORMAL 值。 ARM 平臺和 x64 平臺支援 SSE2,使 DENORMAL 操作數和結果被刷新或強制為零。 **_controlfp_s、_controlfp**和 **_control87**函數提供更改此行為的 **_controlfp**掩碼。 下列範例示範如何使用此遮罩：

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平臺上 **,_controlfp_s**功能適用於 FPSCR 寄存器。 在 x64 體系結構上,只有存儲在 MXCSR 寄存器中的 SSE2 控制字才受到影響。 在英特爾 (x86) 平臺上,**如果存在_controlfp_s**會影響 x87 和 SSE2 的控制詞。 兩個控制詞可能彼此不一致(例如,由於之前對[__control87_2](control87-controlfp-control87-2.md)的調用);如果兩個控制詞之間不一致 **,_controlfp_s***在當前控件*中設置**EM_AMBIGUOUS**標誌。 這警告所傳回的控制字組可能無法精確地呈現這兩個浮點控制字組的狀態。

在 ARM 和 x64 體系結構上,不支援更改無窮大模式或浮點精度。 如果在 x64 平臺上使用精度控制掩碼,則函數將引發斷言並調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如果未正確地設定遮罩，則此函式會產生無效參數例外狀況 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許執行繼續,則此函數將傳回**EINVAL**並將**errno**設定到**EINVAL**。

當您使用[/clr(通用語言運行時編譯)](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時,將忽略此函數,因為通用語言運行時 (CLR) 僅支援預設浮點精度。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="mask-constants-and-values"></a>遮罩常量和值

對於 **_MCW_EM**遮罩,清除它將設置異常,這允許硬體異常;設置它隱藏異常。 如果發生 **_EM_UNDERFLOW**或 **_EM_OVERFLOW,** 則在執行下一個浮點指令之前不會引發任何硬體異常。 要**在_EM_UNDERFLOW**或 **_EM_OVERFLOW**後立即生成硬體異常,請調用 FWAIT MASM 指令。

|Mask|十六進位值|持續性|十六進位值|
|----------|---------------|--------------|---------------|
|**_MCW_DN(** 非正常控制 )|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM(** 中斷異常遮罩 )|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC(** 無限控制 )<br /><br /> (ARM 或 x64 平臺上不受支援。|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC(** 四捨五入控制)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC(** 精確控制 )<br /><br /> (ARM 或 x64 平臺上不受支援。|0x00030000|**_PC_24** (24 位)<br /><br /> **_PC_53** (53 位)<br /><br /> **_PC_64** (64 位)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
