---
title: _controlfp_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _controlfp_s
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
- controlfp_s
- _controlfp_s
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 443b9ee53606bc3075e62e98012edfca79747cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405087"
---
# <a name="controlfps"></a>_controlfp_s

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

*currentControl*<br/>
目前的控制字組位元值。

*newControl*<br/>
新的控制字組位元值。

*遮罩*<br/>
要設定之新控制字組位元的遮罩。

## <a name="return-value"></a>傳回值

如果成功，或零**errno**數值錯誤碼。

## <a name="remarks"></a>備註

**_Controlfp_s**函式是更安全的平台獨立版本的 **_control87**，此 cmdlet 會取得浮點控制字組會儲存在位址*currentControl*並設定使用*newControl*。 值中的位元表示浮點控制狀態。 浮點控制狀態可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式 (視平台而定)。 您也可以使用 **_controlfp_s**要加上遮罩或取消遮罩的浮點例外狀況。

如果值*遮罩*等於 0， **_controlfp_s**取得浮點控制字組，並將擷取的值在*currentControl*。

如果*遮罩*是控制字組的新值會設定為非零，： 針對任何已設定的位元 （也就是等於 1） 在*遮罩*中的對應位元*新*用來更新控制，word。 換句話說， *fpcntrl* = ((*fpcntrl* & ~*遮罩*) &#124; (*newControl* & *遮罩*)) 其中*fpcntrl*是浮點控制字組。 在此案例中， *currentControl*設後的值變更完成，而非舊的控制字組位元值。

> [!NOTE]
> 根據預設，執行階段程式庫會遮罩所有浮點例外狀況。

**_controlfp_s**幾乎完全相同 **_control87** (x86)、 x64 和 ARM 平台上 Intel 函式。 如果您的目標 x86、 x64 或 ARM 平台，您可以使用 **_control87**或 **_controlfp_s**。

之間的差異 **_control87**和 **_controlfp_s**是中如何處理異常值。 Intel (x86)，x64 和 ARM 平台， **_control87**可以設定和清除異常運算元例外狀況遮罩。 **_controlfp_s**不會修改異常運算元例外狀況遮罩。 這個範例示範差異：

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

可能的值遮罩常數 (*遮罩*) 和新控制項的值 (*newControl*) 會顯示在下表的十六進位值。 使用下面所列的可攜式常數 (**_MCW_EM**， **_EM_INVALID**，依此類推) 做為這些函式的引數，而不是提供十六進位值明確。

Intel (x86) 衍生的平台支援硬體中的 DENORMAL 輸入和輸出值。 x86 行為是保留 DENORMAL 值。 ARM 平台和 x64 支援 SSE2 的平台可讓 DENORMAL 運算元和結果，以排清，或為零強制。 **_Controlfp_s**， **_controlfp**，和 **_control87**函式提供的遮罩，若要變更此行為。 下列範例示範如何使用此遮罩：

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

在 ARM 平台， **_controlfp_s**函式適用於在 FPSCR 暫存器。 X64 架構，只 SSE2 控制字組儲存在 MXCSR 暫存器會受到影響。 Intel (x86) 平台上， **_controlfp_s**影響控制項的文字將 x87 和 SSE2，如果有的話。 很可能彼此不一致的兩個單字 (由於先前呼叫[__control87_2](control87-controlfp-control87-2.md)，例如); 如果存在兩個控制字詞之間不一致 **_controlfp_s**設定**EM_AMBIGUOUS**加上旗標*currentControl*。 這警告所傳回的控制字組可能無法精確地呈現這兩個浮點控制字組的狀態。

在 ARM 和 x64 架構，變更無限大模式或浮點精確度不支援。 如果精確度控制遮罩適用於 x64 平台，此函數會引發判斷提示和無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

如果未正確地設定遮罩，則此函式會產生無效參數例外狀況 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，則此函數會傳回**EINVAL**並設定**errno**至**EINVAL**。

當您使用時，此函式會忽略[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯，因為 common language runtime (CLR) 只支援預設的浮點精確度。

### <a name="mask-constants-and-values"></a>遮罩常數和值

如 **_MCW_EM**遮罩，清除設定允許的硬體例外狀況的例外狀況; 將它隱藏例外狀況。 如果 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**就會發生下一步的浮點指令執行之前，會擲回任何硬體例外狀況。 若要產生的硬體例外狀況之後立即 **_EM_UNDERFLOW**或 **_EM_OVERFLOW**，呼叫 FWAIT MASM 指示。

|遮罩|十六進位值|常數|十六進位值|
|----------|---------------|--------------|---------------|
|**_MCW_DN** （異常控制項）|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** （插斷例外狀況遮罩）|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** （無限大控制）<br /><br /> （不支援在 ARM 或 x64 平台。）|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** （捨入控制項）|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** （精確度控制）<br /><br /> （不支援在 ARM 或 x64 平台。）|0x00030000|**_PC_24** （24 位元）<br /><br /> **_PC_53** （53 位元）<br /><br /> **_PC_64** （64 位元）|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
