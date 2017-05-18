---
title: "_RPT、_RPTF、_RPTW、_RPTFW 巨集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: 14
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: ca0ae546af28c342db2e452bec432ced0437738a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 巨集
產生偵錯報表，以追蹤應用程式進度 (僅限偵錯版本)。 請注意，*n* 指定 `args` 中的引數數目，而且可以是 0、1、2、3、4 或 5。  
  
## <a name="syntax"></a>語法  
  
```  
  
      _RPT  
      n  
      (  
   reportType,  
   format,  
...[args]  
);  
_RPTFn(  
   reportType,  
   format,  
   [args]  
);  
_RPTWn(  
   reportType,  
   format   
   [args]  
);  
_RPTFWn(  
   reportType,  
   format   
   [args]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `reportType`  
 報表類型：`_CRT_WARN`、`_CRT_ERROR` 或 `_CRT_ASSERT`。  
  
 `format`  
 用於建立使用者訊息的格式控制字串。  
  
 `args`  
 `format` 使用的替換引數。  
  
## <a name="remarks"></a>備註  
 所有這些巨集接受`reportType`和`format`參數。 此外，它們也可能最多接受四個其他引數，以附加至巨集名稱的號碼表示。 例如，`_RPT0` 和 `_RPTF0` 不接受任何額外引數、`_RPT1` 和 `_RPTF1` 接受 `arg1`，而 `_RPT2` 和 `_RPTF2` 接受 `arg1` 和 `arg2`，以此類推。  
  
 `_RPT` 和 `_RPTF` 巨集類似於 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式，原因是它們可以用來追蹤偵錯程序期間的應用程式進度。 不過，因為這些巨集不需要括在 `#ifdef` 陳述式中，即可避免在應用程式的零售組建中呼叫它們，所以比 `printf` 更具彈性。 這種彈性的達成是使用 [_DEBUG](../../c-runtime-library/debug.md) 巨集；只有在定義 `_DEBUG` 旗標時，才能使用 `_RPT` 和 `_RPTF` 巨集。 若未定義 `_DEBUG` ，將會在前置處理期間移除對這些巨集的呼叫。  
  
 `_RPTW` 和 `_RPTFW` 巨集是這些巨集的寬字元版本。 它們與 `wprintf` 類似，並接受寬字元字串作為引數。  
  
 `_RPT` 巨集會呼叫 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 函式來產生含使用者訊息的偵錯報表。 `_RPTW` 巨集會呼叫 `_CrtDbgReportW` 函式來產生具有寬字元的相同報表。 除了使用者訊息之外，`_RPTF` 和 `_RPTFW` 巨集還會建立內含呼叫報表巨集之原始程式檔和行號的偵錯報表。 使用 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式所定義的相同規則，透過將 `arg`[*n*] 引數取代為 `format` 字串，來建立使用者訊息。  
  
 `_CrtDbgReport` 或 `_CrtDbgReportW` 會根據目前報表模式以及針對 `reportType` 所定義的檔案來產生偵錯報表，並判斷其目的地。 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 和 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。  
  
 如果呼叫 `_RPT` 巨集，而且尚未呼叫 `_CrtSetReportMode` 和 `_CrtSetReportFile`，則訊息顯示如下。  
  
|報表類型|輸出目的地|  
|-----------------|------------------------|  
|`_CRT_WARN`|不會顯示警告文字。|  
|`_CRT_ERROR`|快顯視窗。 與指定 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` 時相同。|  
|`_CRT_ASSERT`|與 `_CRT_ERROR` 相同。|  
  
 如果目的地為偵錯訊息視窗，而且使用者選擇 [重試] 按鈕，若已啟用 Just-in-Time (JIT) 偵錯，則 `_CrtDbgReport` 或 `_CrtDbgReportW` 會傳回 1，讓這些巨集啟動偵錯程式。 如需如何使用這些巨集作為偵錯錯誤處理機制的詳細資訊，請參閱[使用巨集進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。  
  
 有兩個其他巨集可產生偵錯報表。 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集會產生報表，但僅限其運算式引數評估為 FALSE 時。 [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 與 `_ASSERT` 完全相同，但將失敗的運算式併入產生的報表中。  
  
## <a name="requirements"></a>需求  
  
|巨集|必要的標頭|  
|-----------|---------------------|  
|`_RPT` 巨集|\<crtdbg.h>|  
|`_RPTF` 巨集|\<crtdbg.h>|  
|`_RPTW` 巨集|\<crtdbg.h>|  
|`_RPTFW` 巨集|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
 雖然這些都是巨集，並且可透過加入 Crtdbg.h 來取得，但因為這些巨集會呼叫其他執行階段函式，所以應用程式必須連結其中一個偵錯程式庫。  
  
## <a name="example"></a>範例  
 請參閱 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 主題中的範例。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)
