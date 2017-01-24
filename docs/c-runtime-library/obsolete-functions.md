---
title: "過時的函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_wctype"
  - "_loaddll"
  - "_unloaddll"
  - "_getdllprocaddr"
  - "_seterrormode"
  - "_beep"
  - "_sleep"
  - "_getsystime"
  - "corecrt_wctype/is_wctype"
  - "process/_loaddll"
  - "process/_unloaddll"
  - "process/_getdllprocaddr"
  - "stdlib/_seterrormode"
  - "stdlib/_beep"
  - "stdlib/_sleep"
  - "time/_getsystime"
  - "time/_setsystime"
dev_langs: 
  - "C"
  - "C++"
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 過時的函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

某些程式庫函式已經過時，而且有較新的對等用法。 建議您將這些函式變更為更新版本。 其他過時的函式則已從 CRT 移除。 本主題列出因過時而被取代的函式，以及特定版本的 Visual Studio 中已移除的函式。  
  
## Visual Studio 2015 中因過時而被取代的函式  
  
|已過時的函式|替代函式|  
|------------|----------|  
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)、[LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091) 或 [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[Beep](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[Sleep](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## Visual Studio 2015 中已從 CRT 移除的函式  
  
|已過時的函式|替代函式|  
|------------|----------|  
|[\_cgets、\_cgetws](../c-runtime-library/cgets-cgetws.md)|[\_cgets\_s、\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets、\_getws](../c-runtime-library/gets-getws.md)|[gets\_s、\_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[\_get\_output\_format](../c-runtime-library/get-output-format.md)|無|  
|[\_heapadd](../c-runtime-library/heapadd.md)|無|  
|[\_heapset](../c-runtime-library/heapset.md)|無|  
|[inp、inpw](../c-runtime-library/inp-inpw.md)|無|  
|[\_inp、\_inpw、\_inpd](../c-runtime-library/inp-inpw-inpd.md)|無|  
|[outp、outpw](../c-runtime-library/outp-outpw.md)|無|  
|[\_outp、\_outpw、\_outpd](../c-runtime-library/outp-outpw-outpd.md)|無|  
|[\_set\_output\_format](../c-runtime-library/set-output-format.md)|無|  
  
## 舊版 Visual Studio 中已從 CRT 移除的函式  
 [\_lock](../c-runtime-library/lock.md)  
  
 [\_unlock](../c-runtime-library/unlock.md)