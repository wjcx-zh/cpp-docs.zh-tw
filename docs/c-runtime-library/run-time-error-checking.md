---
title: "執行階段錯誤檢查 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "執行階段錯誤檢查"
  - "執行階段錯誤, 檢查"
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 執行階段錯誤檢查
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 執行階段程式庫包含支援執行階段錯誤檢查的函式 \(RTC\)。  執行階段錯誤檢查允許您為程式建立這類特定種類的執行階段錯誤報告。  您指定錯誤的報告，以及型別錯誤報告。  如需詳細資訊，請參閱[執行階段錯誤檢查](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md)。  
  
 使用下列函式自訂您的程式執行階段錯誤檢查的方式。  
  
### 啟用執行階段錯誤檢查。  
  
|功能|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[\_RTC\_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|傳回執行階段錯誤檢查型別的簡短說明。||  
|[\_RTC\_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|會傳回可被執行階段錯誤檢查 \(RTC\) 偵測到的錯誤類型全部數目。||  
|[\_RTC\_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|將函式當做報告執行階段錯誤檢查處理常式。||  
|[\_RTC\_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|關聯由執行階段錯誤檢查以型別偵測的錯誤。||  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [\/RTC \(執行階段錯誤檢查\)](../build/reference/rtc-run-time-error-checks.md)   
 [runtime\_checks](../preprocessor/runtime-checks.md)   
 [RTC sample](http://msdn.microsoft.com/zh-tw/b3415b09-f6fd-43dc-8c02-9a910bc2574e)   
 [偵錯常式](../c-runtime-library/debug-routines.md)