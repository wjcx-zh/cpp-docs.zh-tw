---
title: "_endthread、_endthreadex | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _endthread
- _endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
dev_langs:
- C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: e329acaad53c8990f335394bbcb8f0401d71c463
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="endthread-endthreadex"></a>_endthread、_endthreadex
中止執行緒； `_endthread` 會中止由 `_beginthread` 建立的執行緒，而  `_endthreadex` 會終止由 `_beginthreadex`建立的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### <a name="parameters"></a>參數  
 `retval`  
 執行緒結束代碼。  
  
## <a name="remarks"></a>備註  
 您可以明確地呼叫 `_endthread` 或 `_endthreadex` 來終止執行緒。不過，當執行緒從作為參數傳遞至 `_endthread` 或 `_endthreadex` 的常式傳回時，也會自動呼叫 `_beginthread` 或 `_beginthreadex`。 透過呼叫 `endthread` 或 `_endthreadex` 終止執行緒，有助於確保適當復原配置給執行緒的資源。  
  
> [!NOTE]
>  對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。 `_endthread` 和 `_endthreadex` 會回收配置的執行緒資源，然後呼叫 `ExitThread`。  
  
 `_endthread` 會自動關閉執行緒控制代碼 (此行為與 Win32 `ExitThread` API 不同)。因此，當您使用 `_beginthread` 和 `_endthread` 時，不要藉由呼叫 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API，明確地關閉執行緒控制代碼。  
  
 像 Win32 `ExitThread` API 一樣， `_endthreadex` 不會關閉執行緒控制代碼。 因此，當您使用 `_beginthreadex` 和 `_endthreadex`時，您必須呼叫 Win32 `CloseHandle` API，以關閉執行緒控制代碼。  
  
> [!NOTE]
>  `_endthread` 和 `_endthreadex` 會導致在執行緒中暫止的 C++ 解構函式不會被呼叫。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_endthread`|\<process.h>|  
|`_endthreadex`|\<process.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的多執行緒版本。  
  
## <a name="example"></a>範例  
 請參閱 [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)的範例。  
  
## <a name="see-also"></a>另請參閱  
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_beginthread、_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)
