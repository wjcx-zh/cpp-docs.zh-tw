---
title: raise | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- raise
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
- Raise
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: ff8b387b81487e0c39ba5018487a1b8045bd0574
ms.lasthandoff: 02/24/2017

---
# <a name="raise"></a>raise
將訊號傳送到執行中的程式。  
  
> [!NOTE]
>  除非是測試或偵錯的狀況，否則不要使用這個方法關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889) 的 3.6 節，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 如需詳細資訊，請參閱[應用程式生命週期 (Windows 市集應用程式)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### <a name="parameters"></a>參數  
 *sig*  
 要產生的訊號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，**raise** 會傳回 0。 否則，它會傳回非零值。  
  
## <a name="remarks"></a>備註  
 **raise** 函式傳送 *sig* 給執行中的程式。 如果先前的 **signal** 呼叫已安裝 *sig* 的訊號處理函式，則 **raise** 會執行該函式。 如果尚未安裝任何處理常式函式，會採取與訊號值 *sig* 相關聯的預設動作，如下所示。  
  
|訊號|意義|Default|  
|------------|-------------|-------------|  
|`SIGABRT`|異常終止|結束呼叫程式，結束代碼 3|  
|`SIGFPE`|浮點錯誤|結束呼叫程式|  
|`SIGILL`|不合法的指令|結束呼叫程式|  
|`SIGINT`|CTRL+C 中斷|結束呼叫程式|  
|`SIGSEGV`|不合法的儲存體存取|結束呼叫程式|  
|`SIGTERM`|終止傳送給程式的要求|忽略訊號|  
  
 如果引數不是有效的訊號，如上述所指定，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果未處理，則此函式會將 `errno` 設為 `EINVAL` 並傳回非零值。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|**raise**|\<signal.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [signal](../../c-runtime-library/reference/signal.md)
