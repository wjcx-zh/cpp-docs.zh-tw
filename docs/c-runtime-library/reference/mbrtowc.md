---
title: mbrtowc
ms.date: 11/04/2016
api_name:
- mbrtowc
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: b4c68ae8df9821d862b9f742d8a8ef7ace19c981
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952435"
---
# <a name="mbrtowc"></a>mbrtowc

將目前地區設定的多位元組字元轉換成對等的寬字元，並提供在多位元組字元中間重新啟動的功能。

## <a name="syntax"></a>語法

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>參數

*wchar*<br/>
用來接收已轉換寬字元字串（類型**wchar_t**）之寬字元的位址。 如果不需要傳回任何寬字元，這個值可以是 null 指標。

*mbchar*<br/>
位元組序列 (多位元組字元) 的位址。

*計數*<br/>
要檢查的位元組數目。

*mbstate*<br/>
轉換狀態物件的指標。 如果這個值是 null 指標，函式會使用靜態內部轉換狀態物件。 由於內部**mbstate_t**物件不是安全線程，因此建議您一律傳遞自己的*mbstate*引數。

## <a name="return-value"></a>傳回值

下列其中一個值：

0如果*wchar*不是 null 指標，則下一個*計數*或較少的位元組會完成代表 null 寬字元的多位元組字元（儲存在*wchar*中）。

1以*計數*，包含下一個*計數*或較少個位元組，完成有效的多位元組字元。 傳回的值是完成多位元組字元的位元組數目。 如果*wchar*不是 null 指標，則對等的寬字元會儲存在*wchar*中。

（size_t）（-1）發生編碼錯誤。 下一個*計數*或較少的位元組不會參與完整且有效的多位元組字元。 在此情況下， **errno**會設定為 EILSEQ，而*mbstate*中的轉換移位狀態則為未指定。

（size_t）（-2）下一個*計數*位元組有助於不完整但可能是有效的多位元組字元，而且所有的*計數*位元組都已經處理。 *Wchar*中不會儲存任何值，但會更新*mbstate*以重新開機函數。

## <a name="remarks"></a>備註

如果*mbchar*為 null 指標，則函式相當於呼叫：

`mbrtowc(NULL, "", 1, &mbstate)`

在此情況下，會忽略引數*wchar*和*count*的值。

如果*mbchar*不是 null 指標，此函式會檢查來自*mbchar*的*count*個位元組，以判斷完成下一個多位元組字元所需的必要位元組數目。 如果下一個字元是有效的，則對應的多位元組字元會儲存在*wchar*中（如果不是 null 指標）。 如果字元是對應的寬 null 字元， *mbstate*的產生狀態就是初始轉換狀態。

**解譯 mbrtowc**函式與[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)的重新開機功能不同。 轉換狀態會儲存在*mbstate*中，以供後續呼叫相同或其他可重新開機的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用**wcsrtombs**的後續呼叫，而不是**wcstombs**，則應用程式應該使用**wcsrlen**而不是**wcslen** 。

## <a name="example"></a>範例

將多位元組字元轉換成其對等的寬字元。

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>範例輸出

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
