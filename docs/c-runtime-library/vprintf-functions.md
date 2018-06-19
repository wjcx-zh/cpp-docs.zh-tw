---
title: vprintf 函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- vprintf
dev_langs:
- C++
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d63e5da79b0f78e701f3ababaf54bef41fbf88a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418376"
---
# <a name="vprintf-functions"></a>vprintf 函式
每個 `vprintf` 函式都會接受引數清單的指標，然後設定指定資料的格式，並將其寫入到特定目的地。 函式在執行參數驗證方面有所不同，取決於函式接受寬字元字串或單一位元組字元字串、輸出目的地，以及是否支援在參數所在格式字串中指定順序。  
  
|||  
|-|-|  
|[_vcprintf、_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf、_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## <a name="remarks"></a>備註  
 `vprintf` 函式類似下表所列的對應函式。 然而，每個 `vprintf` 函式都接受引數清單的指標，而每個對應函式都接受引數清單。  
  
 這些函式會設定要輸出到目的地的資料格式，如下所示。  
  
|功能|對應函式|輸出目的地|參數驗證|位置參數支援|  
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|  
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|主控台|檢查是否 Null。|否|  
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|主控台|檢查是否 Null。|否|  
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*資料流*|檢查是否 Null。|否|  
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*資料流*|檢查 Null 與有效格式。|是|  
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*資料流*|檢查 Null 與有效格式。|否|  
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*資料流*|檢查是否 Null。|否|  
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*資料流*|檢查 Null 與有效格式。|是|  
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*資料流*|檢查 Null 與有效格式。|否|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|檢查是否 Null。|否|  
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|檢查 Null 與有效格式。|是|  
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|檢查 Null 與有效格式。|否|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|檢查是否 Null。|否|  
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|檢查 Null 與有效格式。|是|  
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|檢查 Null 與有效格式。|否|  
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|由 *buffer* 所指向的記憶體|檢查是否 Null。|否|  
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|由 *buffer* 所指向的記憶體|檢查 Null 與有效格式。|是|  
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|由 *buffer* 所指向的記憶體|檢查 Null 與有效格式。|否|  
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|由 *buffer* 所指向的記憶體|檢查是否 Null。|否|  
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|由 *buffer* 所指向的記憶體|檢查 Null 與有效格式。|是|  
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|由 *buffer* 所指向的記憶體|檢查 Null 與有效格式。|否|  
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|由 *buffer* 所指向的記憶體|檢查是否 Null。|否|  
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|由 *buffer* 所指向的記憶體|檢查是否 Null。|否|  
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|由 *buffer* 所指向的記憶體|檢查是否 Null。|否|  
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|由 *buffer* 所指向的記憶體|檢查是否 Null。|否|  
  
 `argptr` 引數的類型是 `va_list`，它是在 VARARGS.H 與 STDARG.H 中所定義。 `argptr` 變數必須由 **va_start** 初始化，而且可能由後續 `va_arg` calls; `argptr` 重新初始化，然後根據 *format* 引數中的對應規格指向已針對輸出而轉換並傳輸的引數清單開頭。 *format* 具有與 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 之 *format* 引數相同的形式與功能。 這些函式都不會叫用 `va_end`。 如需有關每個 `vprintf` 函式的完整描述，請參閱上表所列之對應函式的描述。  
  
 `_vsnprintf` 與 **vsprintf** 不同，因為它不會寫入超過 *count* 個位元組到 *buffer*。  
  
 這些名稱中含有 **w** 字元的函式版本是名稱中不含 **w** 字元之對應函式的寬字元版本；在這些寬字元函式中，*buffer* 與 *format* 是寬字元字串。 否則，每個寬字元函式的運作方式與其 SBCS 對應函式的運作方式相同。  
  
 這些名稱具有 **_s** 與 **_p** 尾碼的函式版本是較安全的版本。 這些版本會驗證格式字串，而且會在格式字串的格式不正確 (例如，使用格式無效的字元) 時產生例外狀況。  
  
 這些名稱具有 **_p** 尾碼的函式版本可讓您指定在格式字串中代換所指定引數的順序。 如需詳細資訊，請參閱 [printf_p 位置參數](../c-runtime-library/printf-p-positional-parameters.md)。  
  
 針對 **vsprintf**、`vswprintf`、`_vsnprintf` 與 `_vsnwprintf`，如果在重疊的字串之間進行複製，則行為是未定義的。  
  
> [!IMPORTANT]
>  確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 若使用這些函式的安全版本 (不論是 **_s** 或 **_p** 尾碼)，使用者提供的格式字串可能觸發無效的參數例外狀況 (若使用者提供的字串包含無效的格式設定字元)。  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../c-runtime-library/stream-i-o.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg、va_copy、va_end、va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)