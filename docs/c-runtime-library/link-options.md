---
title: "連結選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "nothrownew.obj"
  - "newmode.obj"
  - "noenv.obj"
  - "psetargv.obj"
  - "loosefpmath.obj"
  - "smallheap.obj"
  - "fp10.obj"
  - "nochkclr.obj"
  - "chkstk.obj"
  - "pcommode.obj"
  - "pnoenv.obj"
  - "連結選項 [C++]"
  - "invalidcontinue.obj"
  - "pnothrownew.obj"
  - "pwsetargv.obj"
  - "pinvalidcontinue.obj"
  - "wsetargv.obj"
  - "binmode.obj"
  - "setargv.obj"
  - "noarg.obj"
  - "pnewmode.obj"
  - "commode.obj"
  - "pthreadlocale.obj"
  - "pbinmode.obj"
  - "threadlocale.obj"
  - "pnoarg.obj"
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結選項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

CRT lib 目錄包含一些小目的檔使得無須改變任何程式碼即能啟用特定的 CRT 功能。  它們被稱為「連結選項」 \(link options\) ，因為您只須在連結命令列中加入它們即可使用。  
  
 已加入純粹模式的版本。  在本地或 \/clr 程式碼中使用一般版本， \/clr::pure 模式則使用純粹版本 \(以一個 p 前綴\) 。  
  
|原生 和 \/clr|純粹模式|描述|  
|----------------|----------|--------|  
|binmode.obj|pbinmode.obj|將預設的檔案翻譯模式轉為二元。  請參閱 [\_fmode](../c-runtime-library/fmode.md)。|  
|chkstk.obj|N\/A|在不使用 CRT 時提供堆疊檢查和 alloca 的支援。|  
|commode.obj|pcommode.obj|將全域套用旗標設為「套用 \(commit\) 」。  請參閱[fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)和[fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)。|  
|fp10.obj|N\/A|變更預設的精準度控制為 64 位元。  請參閱 [浮點支援](../c-runtime-library/floating-point-support.md)。|  
|invalidcontinue.obj|pinvalidcontinue.obj|設定預設沒有任何動作的無效參數處理常式，這意味傳遞無效的參數予 CRT 函式只會導致 error 被設置並回傳錯誤結果。|  
|loosefpmath.obj|N\/A|確保程式碼浮點數可以接受非正規化數值。|  
|newmode.obj|pnewmode.obj|失敗時，導致 [malloc](../c-runtime-library/reference/malloc.md) 呼叫新的處理常式。  請參閱 [\_set\_new\_mode](../c-runtime-library/reference/set-new-mode.md)、[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)、[calloc](../c-runtime-library/reference/calloc.md) 和 [realloc](../c-runtime-library/reference/realloc.md)。|  
|noarg.obj|pnoarg.obj|停用所有 argc 和 argv 的處理。|  
|nochkclr.obj|N\/A|不執行任何動作。  從專案中移除。|  
|noenv.obj|pnoenv.obj|停止為 CRT 建立快取環境。|  
|nothrownew.obj|pnothrownew.obj|啟用 CRT 裏非擲回例外狀況版本的 new 。  請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)。|  
|setargv.obj|psetargv.obj|啟用命令列參數的外卡敍述式。  請參閱 [展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。|  
|smalheap.obj|N\/A|安裝非常簡易的小型堆積管理器。|  
|threadlocale.obj|pthreadlocale.obj|啟用預設每個新執行緒的地區設定。|  
|wsetargv.obj|pwsetargv.obj|啟用命令列參數的外卡敍述式。  請參閱 [展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。|  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)