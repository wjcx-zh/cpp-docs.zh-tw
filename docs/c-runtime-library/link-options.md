---
title: 連結選項 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7cccd76f428ea2e1234a0e2da54452c051e683d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="link-options"></a>連結選項
CRT lib 目錄包含多個小型物件檔案，不需要變更任何程式碼即可啟用特定的 CRT 功能。 它們稱之為「連結選項」，因為它們必須加入連結器命令列才能使用。  
  
 純模式版本已自 Visual Studio 2015 起淘汰。 請使用機器碼與 /clr 程式碼的一般版本。  
  
|原生和 /clr|純的模式|描述|  
|----------------------|---------------|-----------------|  
|binmode.obj|pbinmode.obj|將預設檔案轉譯模式設為二進位。 請參閱 [_fmode](../c-runtime-library/fmode.md)。|  
|chkstk.obj|N/A|不使用 CRT 時提供堆疊檢查和 alloca 支援。|  
|commode.obj|pcommode.obj|將全域認可旗標設定為「認可」。 請參閱 [fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md) 和 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)。|  
|fp10.obj|N/A|將預設的精確度控制變更為 64 位元。 請參閱[浮點支援](../c-runtime-library/floating-point-support.md)。|  
|invalidcontinue.obj|pinvalidcontinue.obj|設定不做任何動作的預設無效的參數處理常式，表示傳遞至 CRT 函式的無效參數只會設定 errno 並傳回錯誤結果。|  
|loosefpmath.obj|N/A|確保浮點程式碼容許異常值。|  
|newmode.obj|pnewmode.obj|使 [malloc](../c-runtime-library/reference/malloc.md) 在失敗時呼叫新的處理常式。 請參閱 [_set_new_mode](../c-runtime-library/reference/set-new-mode.md)、[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)、[calloc](../c-runtime-library/reference/calloc.md) 和 [realloc](../c-runtime-library/reference/realloc.md)。|  
|noarg.obj|pnoarg.obj|停用所有的 argc 和 argv 處理。|  
|nochkclr.obj|N/A|不執行任何動作 從專案中移除。|  
|noenv.obj|pnoenv.obj|停用建立 CRT 快取環境。|  
|nothrownew.obj|pnothrownew.obj|啟用 CRT 的非擲回版本新功能。 請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)。|  
|setargv.obj|psetargv.obj|啟用命令列引數萬用字元展開。 請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。|  
|threadlocale.obj|pthreadlocale.obj|所有的新執行緒預設啟用每個執行緒地區設定。|  
|wsetargv.obj|pwsetargv.obj|啟用命令列引數萬用字元展開。 請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。|  
  
## <a name="see-also"></a>請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)