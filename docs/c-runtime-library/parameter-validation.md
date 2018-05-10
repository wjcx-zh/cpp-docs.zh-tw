---
title: 參數驗證 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a89ec2cd0b360f498e52af7e49bd5c6571521e2c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-validation"></a>參數驗證
大部分的安全性增強 CRT 函式和許多預先存在的函式都會驗證其參數。 這可能包括檢查 NULL 指標、檢查落在有效範圍的整數，或檢查列舉值是否有效。 找到無效的參數時，就會執行無效的參數處理常式。  
  
## <a name="invalid-parameter-handler-routine"></a>無效的參數處理常式  
 當 C 執行階段程式庫函式偵測到無效的參數時，它會擷取有關此錯誤的某些資訊，然後呼叫包裝無效參數處理常式分派函式的巨集，是 [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md)、[_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md) 或 [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md) 的其中之一。 呼叫的分派函式隨您的程式碼為偵錯版、零售版，或錯誤不視為可復原而定。 
 
 偵錯版中，無效的參數巨集通常會在呼叫分派函式之前，引發失敗的判斷提示和偵錯工具中斷點。 執行程式碼時，可能會在具有 [中止]、[重試] 和 [繼續] 或類似選項的對話方塊中向使用者報告判斷提示，視作業系統和執行階段程式庫版本而定。 這些選項可讓使用者立即終止程式、附加偵錯工具，或讓現有的程式碼繼續執行，它會呼叫分派函式。 
 
 無效的參數處理常式分派函式接著會呼叫目前指派的無效參數處理常式。 根據預設，無效的參數會呼叫造成應用程式「損毀」的 `_invoke_watson`，亦即終止並產生小型傾印。 如果是由作業系統啟用，對話方塊會詢問使用者是否要載入損毀傾印供 Microsoft 分析。   
  
 使用函式 [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 或 [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 將無效的參數處理常式設成您自己的函式，可以變更此行為。 如果您指定的函式不終止應用程式，控制權就會回到接收了無效參數的函式。 在 CRT 中，這些函式通常會停止執行函數，將 `errno` 設為錯誤碼，並傳回錯誤碼。 在許多情況下，`errno` 值和傳回值都是指出無效參數的 `EINVAL`。 在某些情況下，會傳回更具體的錯誤碼，例如不正確檔案指標的 `EBADF` 傳入為參數。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="see-also"></a>請參閱  
 [CRT 的安全性功能](../c-runtime-library/security-features-in-the-crt.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)