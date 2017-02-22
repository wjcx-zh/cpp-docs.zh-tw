---
title: "偵錯常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯 [CRT]，使用巨集"
  - "巨集，偵錯工具"
  - "偵錯常式"
  - "偵錯巨集"
  - "偵錯 [CRT]，執行階段常式"
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 偵錯常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 執行階段程式庫的偵錯版本，提可偵錯程式更容易給開發人員許多的診斷服務:  
  
-   步驟直接加入至在偵錯期間的執行階段函式。  
  
-   解析聲明、錯誤和例外狀況。  
  
-   追蹤堆積配置並防止記憶體遺漏。  
  
-   報告偵錯訊息給使用者。  
  
 若要使用這些常式，就必須定義 [\_DEBUG](../c-runtime-library/debug.md) 旗標。  所有在應用程式的零售版本中的這些常式不會執行任何動作。  如需如何使用新的偵錯常式的詳細資訊，請參閱 [CRT 偵錯技術。](../Topic/CRT%20Debugging%20Techniques.md)。  
  
### 偵錯 C 執行階段程式庫常式的版本  
  
|常式|使用|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[\_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|當結果為 false 時，請評估運算式並產生偵錯報告|[\<caps:sentence id\="tgt15" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|與 `_ASSERT`類似，不過，在產生的報告中失敗的運算式|[\<caps:sentence id\="tgt18" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|檢查配置的記憶體區塊的完整性在偵錯堆積|[\<caps:sentence id\="tgt20" sentenceid\="e42975224af21ff11a761e6a6bdbd602" class\="tgtSentence"\>System::Diagnostics::PerformanceCounter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[\_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|設定中斷點。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtDbgReport、\_CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|產生與使用者訊息的偵錯報告並傳送報告為三個可能的目的端。|[System::Diagnostics::Debug::Write](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.write.aspx)， [System::Diagnostics::Debug::Writeline](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeline.aspx)， [System::Diagnostics::Debug::WriteIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeif.aspx)， [System::Diagnostics::Debug::WriteLineIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writelineif.aspx)|  
|[\_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|呼叫任何 `_CLIENT_BLOCK` 型別之應用程式所提供的函式在堆積|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|當一個重大記憶體遺漏的情形發生時，請傾印所有記憶體區塊在偵錯堆積|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|確認指定的記憶體區塊會在本機堆積中，而且有有效偵錯堆積區塊類型的識別項。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|確認指定的指標在本機堆積|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|確認指定的記憶體範圍為讀取和寫入有效|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|取得偵錯堆積的目前狀態並將它儲存在應用程式所提供的 `_CrtMemState` 結構。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|比較重大差異的兩個記憶體狀態並傳回結果。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|做為指定的檢查點採用或從啟動程式執行，請傾印與物件有關的資訊在堆積|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|傾印從上一個指定的記憶體狀態的偵錯標頭資訊以使用者可閱讀的格式|[\<caps:sentence id\="tgt64" sentenceid\="e42975224af21ff11a761e6a6bdbd602" class\="tgtSentence"\>System::Diagnostics::PerformanceCounter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[\_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|傳回與指定的偵錯堆積區塊指標相關聯的區塊類型\/子類型。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|您可以安裝一個客戶設置函示藉由將它安裝在 C 執行時間偵錯記憶體配置階段上。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|設定所指定的物件設定順序編號上設定中斷點|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|擷取或修改 `_crtDbgFlag` 旗標狀態控制偵錯堆積管理員的配置行為。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|安裝每次偵錯傾印函式呼叫傾印 `_CLIENT_BLOCK` 型別記憶體區塊的應用程式定義的函式|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|識別檔案或資料流做為目的地為特定報告型別 `_CrtDbgReport`。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|您可以將它安裝用戶端定義的報告函式進入執行階段的 C\# 偵錯報告流程|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportHook2、\_CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|您可以安裝或解除安裝一個客戶報告函示藉由將它安裝在 C 執行時間偵錯報告階段上。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|為 `_CrtDbgReport`所產生之特定報告類型指定一般目的。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|藉由產生偵錯報告追蹤應用程式的處理序可以使用格式字串和引數的變數數字的 `_CrtDbgReport` 。  不提供原始程式檔和行號資訊。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_RPTF &#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|類似於 `_RPTn` 巨集，不過，提供報告起始要求的原始程式檔名稱和行號|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_calloc\_dbg](../c-runtime-library/reference/calloc-dbg.md)|配置的記憶體區塊的指定數目堆積中與偵錯標頭的額外空間並覆寫緩衝區|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_expand\_dbg](../c-runtime-library/reference/expand-dbg.md)|您可以展開或壓縮區塊調整在堆積上配置指定的記憶體區塊。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_free\_dbg](../c-runtime-library/reference/free-dbg.md)|釋放在堆積上的記憶體區塊。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_fullpath\_dbg、\_wfullpath\_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|建立絕對或完整路徑名稱指定的相對路徑名稱，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體。|[\<caps:sentence id\="tgt129" sentenceid\="57f5d14fd2f1847b8e44146f72e48f72" class\="tgtSentence"\>System::IO::File::Create\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[\_getcwd\_dbg、\_wgetcwd\_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|取得目前的工作目錄，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md)|配置的記憶體區塊的盒子堆積中與偵錯標頭的額外空間並覆寫緩衝區|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_msize\_dbg](../c-runtime-library/reference/msize-dbg.md)|計算的記憶體區塊的堆積的大小。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_realloc\_dbg](../c-runtime-library/reference/realloc-dbg.md)|您可以移動或調整區塊重新配置在堆積上配置指定的記憶體區塊。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_strdup\_dbg、\_wcsdup\_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|重複字串，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體。|[\<caps:sentence id\="tgt151" sentenceid\="74a4ca1462af4bfed5950888b5c554e1" class\="tgtSentence"\>System::String::Clone\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)|  
|[\_tempnam\_dbg、\_wtempnam\_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|您可以使用建立暫存檔產生名稱，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 配置記憶體。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
 偵錯常式可以用來對大部分的原始程式碼逐步執行其他 C 執行階段常式在偵錯處理序中。  不過， Microsoft 視為一些技術為私用的，而且，因此，為這些常式不提供原始程式碼。  大部分常式屬於例外狀況處理或浮點管理群組，不過一些的其他也有包含。  這些常規如下表所列。  
  
### 無法使用以原始程式碼形式的 C 執行階段常式  
  
||||  
|-|-|-|  
|[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[\_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|[\_nextafter](../c-runtime-library/reference/nextafter-functions.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[atan， atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[\_fpreset](../c-runtime-library/reference/fpreset.md)|[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)\*|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[\_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[\_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\*|  
|[\_chgsign、\_chgsignf、\_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[\_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[\_clear87、\_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[\_j0](../misc/bessel-functions-j0-j1-jn.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[\_j1](../misc/bessel-functions-j0-j1-jn.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign、copysignf、copysignl、\_copysign、\_copysignf、\_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[\_jn](../misc/bessel-functions-j0-j1-jn.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[\_status87， \_statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[\_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[\_y0](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[\_finite](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[\_y1](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[\_matherr](../c-runtime-library/reference/matherr.md)|[\_yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \*雖然原始程式碼的大部分可用這個常式，它會呼叫內部呼叫原始程式碼未提供的另一個常式。  
  
 某些 C 執行階段函式和 C\+\+ 運算子的行為，當呼叫應用程式的偵錯組建不同。\(應用程式偵錯組建可以定義 `_DEBUG` 旗標或由連結至 C 執行階段程式庫偵錯版本\) 的注意事項。行為差異通常包括常式或資訊提供的額外功能支援偵錯處理序。  這些常規如下表所列。  
  
### 在應用程式的偵錯組建不同行為的常式  
  
|||  
|-|-|  
|C[中止](../c-runtime-library/reference/abort.md) 常式|C\+\+[刪除](../cpp/delete-operator-cpp.md)運算子|  
|C[判斷提示](../c-runtime-library/reference/assert-macro-assert-wassert.md) 常式|C\+\+ [新的](../cpp/new-operator-cpp.md)運算子|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [執行階段錯誤檢查](../c-runtime-library/run-time-error-checking.md)