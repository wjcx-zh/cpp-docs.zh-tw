---
title: 已淘汰的函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: conceptual
f1_keywords:
- is_wctype
- _loaddll
- _unloaddll
- _getdllprocaddr
- _seterrormode
- _beep
- _sleep
- _getsystime
- corecrt_wctype/is_wctype
- process/_loaddll
- process/_unloaddll
- process/_getdllprocaddr
- stdlib/_seterrormode
- stdlib/_beep
- stdlib/_sleep
- time/_getsystime
- time/_setsystime
dev_langs:
- C++
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6fcb14a91aadb01d3962758b19ce636fddfbe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391531"
---
# <a name="obsolete-functions"></a>過時的函式
某些程式庫函式已經過時，而且有較新的對等用法。 建議您將這些函式變更為更新版本。 其他過時的函式則已從 CRT 移除。 本主題列出因過時而被取代的函式，以及特定版本的 Visual Studio 中已移除的函式。  
  
## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Visual Studio 2015 中因過時而被取代的函式  
  
|已過時的函式|替代函式|  
|-----------------------|-----------------|  
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)、 [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091)或 [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[Beep](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[Sleep](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Visual Studio 2015 中已從 CRT 移除的函式  
  
|已過時的函式|替代函式|  
|-----------------------|-----------------|  
|[_cgets、_cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets、_getws](../c-runtime-library/gets-getws.md)|[gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[_get_output_format](../c-runtime-library/get-output-format.md)|無|  
|[_heapadd](../c-runtime-library/heapadd.md)|無|  
|[_heapset](../c-runtime-library/heapset.md)|無|  
|[inp、inpw](../c-runtime-library/inp-inpw.md)|無|  
|[_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)|無|  
|[outp、outpw](../c-runtime-library/outp-outpw.md)|無|  
|[_outp、_outpw、_outpd](../c-runtime-library/outp-outpw-outpd.md)|無|  
|[_set_output_format](../c-runtime-library/set-output-format.md)|無|  
  
## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>舊版 Visual Studio 中已從 CRT 移除的函式  
 [_lock](../c-runtime-library/lock.md)  
  
 [_unlock](../c-runtime-library/unlock.md)