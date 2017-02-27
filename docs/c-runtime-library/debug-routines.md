---
title: "偵錯常式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], run-time routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: fc61db0c2078432ab32030ce897884275d8d2084

---
# <a name="debug-routines"></a>偵錯常式
C 執行階段程式庫的偵錯版本提供許多診斷服務，使得偵錯程式容易使用，並允許開發人員︰  
  
-   在偵錯期間直接進入執行階段函式  
  
-   解決判斷提示、錯誤和例外狀況  
  
-   追蹤堆積配置及預防記憶體流失  
  
-   向使用者報告偵錯訊息  
  
 若要使用這些常式，必須定義 [_DEBUG](../c-runtime-library/debug.md) 旗標。 所有這些常式在應用程式的零售版中不執行任何動作。 如需如何使用新的偵錯常式的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。  
  
### <a name="debug-versions-of-the-c-run-time-library-routines"></a>C 執行階段程式庫常式的偵錯版本  
  
|常式|用法|.NET Framework 同等|  
|-------------|---------|-------------------------------|  
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|評估運算式，並在結果為 FALSE 時產生偵錯報告|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|類似 `_ASSERT`，但產生的報表中會包含失敗的運算式。|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|確認偵錯堆積中配置的記憶體區塊完整性|[System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|設定中斷點。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtDbgReport、_CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|產生具有使用者訊息的偵錯報表，並將報表傳送至三個可能的目的地。|[System::Diagnostics::Debug::Write](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.write.aspx)、[System::Diagnostics::Debug::Writeline](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeline.aspx)、[System::Diagnostics::Debug::WriteIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeif.aspx)、[System::Diagnostics::Debug::WriteLineIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writelineif.aspx)|  
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|針對堆積中的所有 `_CLIENT_BLOCK` 類型呼叫應用程式提供的函式|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|發生嚴重的記憶體流失時，傾印偵錯堆積所有的記憶體區塊。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|確認指定的記憶體區塊位於本機堆積內，且具有有效的偵錯堆積區塊類型識別項。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|確認本機堆積中有指定的指標|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|驗證指定的記憶體範圍是否可有效用於讀取和寫入|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|取得偵錯堆積的目前狀態，並儲存在應用程式提供的 `_CrtMemState` 結構中。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|比較兩個記憶體狀態是否有重大差異並傳回結果|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|傾印堆積物件自採用的指定檢查點之後，或從程式執行開始的資訊。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|以使用者可讀的格式，傾印指定記憶體狀態的偵錯標頭資訊。|[System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|傳回與指定偵錯堆積區塊指標相關聯的區塊類型/子類型。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|將用戶端定義的配置函式連結到 C 執行階段偵錯記憶體配置處理序，以進行安裝。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|在指定的物件配置順序編號設定中斷點|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|擷取或修改 `_crtDbgFlag` 旗標的狀態，以控制偵錯堆積管理員的配置行為。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|安裝應用程式定義的函式，每次呼叫偵錯傾印函式傾印 `_CLIENT_BLOCK` 類型記憶體區塊時都會呼叫此函式。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|找出要依 `_CrtDbgReport` 用為特定報表類型目的地的檔案或資料流|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|將用戶端定義的報告函式連結到 C 執行階段偵錯報告處理序，以進行安裝。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportHook2、_CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|將用戶端定義的報告函式連結到 C 執行階段偵錯報告處理序，以進行安裝或解除安裝。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|指定 `_CrtDbgReport` 產生的特定報表類型的一般目的地|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|呼叫有格式字串和可變引數數目的 `_CrtDbgReport` 產生偵錯報表，來追蹤應用程式的進度。 不提供任何來源檔案和行號資訊。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|類似 `_RPTn` 巨集，但提供提出報告要求的來源檔案名稱和行號。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|針對偵錯標頭和覆寫緩衝區，使用額外空間在堆積中配置指定的記憶體區塊數。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|以展開或收縮區塊的方式，調整堆積的指定記憶體區塊大小。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|釋放堆積的記憶體區塊|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_fullpath_dbg、_wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體，為指定的相對路徑名稱建立絕對或完整路徑名稱。|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_getcwd_dbg、_wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體，取得目前的工作目錄。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|針對偵錯標頭和覆寫緩衝區，使用額外空間在堆積中配置記憶體區塊。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|計算堆積的記憶體區塊大小|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|以移動及/或調整區塊大小的方式，重新配置堆積的指定記憶體區塊。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_strdup_dbg、_wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體，重複字串。|[System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)|  
|[_tempnam_dbg、_wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體，產生可用以建立暫存檔案的名稱。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
 在偵錯過程中，偵錯常式可以用來逐步執行大部分其他 C 執行階段常式的原始程式碼。 不過，Microsoft 考慮到有些技術是有專利的，因此，不提供這些常式的原始程式碼。 這些常式大部分屬於例外狀況處理或浮點處理群組，但也包含少數的其他類型。 下表會列出這些常式。  
  
### <a name="c-run-time-routines-that-are-not-available-in-source-code-form"></a>原始程式碼表單不提供的 C 執行階段常式  
  
||||  
|-|-|-|  
|[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[atan、atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 以及 [printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)*|  
|[_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 以及 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)*|  
|[_chgsign、_chgsignf、_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[_clear87、_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_j0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[_control87、_controlfp、\__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[_j1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[_jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[_status87、_statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[_y0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[_finite](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[_y1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[_yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \*雖然這個常式大多數提供原始程式碼，但它會在內部呼叫另一個不提供原始程式碼的常式。  
  
 從應用程式的偵錯組建呼叫時，某些 C 執行階段函式和 C++ 運算子的行為會不一樣。 (請注意，您可以定義 `_DEBUG` 旗標或連結 C 執行階段程式庫的偵錯版本，來完成應用程式偵錯版。)行為差異通常包含常式提供的額外功能或資訊，以支援偵錯程序。 下表會列出這些常式。  
  
### <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>應用程式偵錯版中行為不同的常式  
  
|||  
|-|-|  
|C [abort](../c-runtime-library/reference/abort.md) 常式|C++ [delete](../cpp/delete-operator-cpp.md) 運算子|  
|C [assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 常式|C++ [new](../cpp/new-operator-cpp.md) 運算子|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [執行階段錯誤檢查](../c-runtime-library/run-time-error-checking.md)


<!--HONumber=Feb17_HO4-->


