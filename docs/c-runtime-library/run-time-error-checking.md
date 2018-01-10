---
title: "執行階段錯誤檢查 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.runtime
dev_langs: C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 981e8c04b305ccef12a463b0a4defd3017916b82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="run-time-error-checking"></a>執行階段錯誤檢查
C 執行階段程式庫包含支援執行階段錯誤檢查 (RTC) 的函式。 執行階段錯誤檢查可讓您建置您的程式報告特定類型的執行階段錯誤。 您要指定報告錯誤的方式，以及報告哪些類型的錯誤。 如需詳細資訊，請參閱[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。  
  
 使用下列函式來自訂您的程式執行執行階段錯誤檢查的方式。  
  
### <a name="run-time-error-checking-functions"></a>執行階段錯誤檢查函式  
  
|功能|使用|  
|--------------|---------|  
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|傳回執行階段錯誤檢查類型的簡短描述。|  
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|傳回執行階段錯誤檢查可以偵測到的錯誤數總計。|  
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|指定函式做為報告執行階段錯誤檢查的處理常式。|  
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|將執行階段錯誤檢查所偵測到的錯誤與類型建立關聯。|  
  
## <a name="see-also"></a>請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [/RTC (執行階段錯誤檢查)](../build/reference/rtc-run-time-error-checks.md)   
 [runtime_checks](../preprocessor/runtime-checks.md)   
 [偵錯常式](../c-runtime-library/debug-routines.md)