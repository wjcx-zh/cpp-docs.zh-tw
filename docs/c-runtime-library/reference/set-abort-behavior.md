---
title: _set_abort_behavior | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: edf31ccddfb9ab2eaa6de226ff4ec7eb09869438
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="setabortbehavior"></a>_set_abort_behavior
指定要在程式異常終止時採取的動作。  
  
> [!NOTE]
>  除非是測試或偵錯的狀況，否則請不要使用 `abort` 函式來關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889)，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 如需詳細資訊，請參閱[應用程式生命週期 (Windows 市集應用程式)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `flags`  
 `abort` 旗標的新值。  
  
 [in] `mask`  
 要設定之 `abort` 旗標位元的遮罩。  
  
## <a name="return-value"></a>傳回值  
 旗標的舊值。  
  
## <a name="remarks"></a>備註  
 有兩個 `abort` 旗標：`_WRITE_ABORT_MSG` 和 `_CALL_REPORTFAULT`。 `_WRITE_ABORT_MSG` 決定是否要在程式異常終止時列印有用的文字訊息。 此訊息說明應用程式已呼叫 `abort` 函式。 預設行為是列印訊息。 `_CALL_REPORTFAULT` 若設定，可指定在呼叫 `abort` 時產生並回報 Watson 損毀傾印。 根據預設，會在非偵錯組建中啟用損毀傾印報告。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_set_abort_behavior`|\<stdlib.h>|  
  
 如需相容性詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```C  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
```Output  
Suppressing the abort message. If successful, this message will be the only output.  
```  
  
## <a name="see-also"></a>另請參閱  
 [abort](../../c-runtime-library/reference/abort.md)
