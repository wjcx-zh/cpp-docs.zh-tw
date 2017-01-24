---
title: "參數驗證 | Microsoft Docs"
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
  - "參數, 驗證"
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 參數驗證
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部份的安全強化 CRT 函式和許多之前已存在的函式會驗證它們的參數。  它們可能包含檢查 NULL 指標，檢查整數是否在有效範圍內，或檢查列舉值是有效的。  當發現無效參數時將會執行無效參數處理常式。  
  
## 無效參數處理常式  
 C 執行階段在發現無效參數時的行為是呼叫目前指定的無效參數處理常式。  預設的無效參數處理常式調用 Watson 當機報告，它會導致應用程式當機並詢問使用者是否要載入當機堆疊傾印予微軟分析。  在偵錯模式下，無效參數也會導致斷言失敗。  
  
 這個行為也可以透過使用 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 函式來將無效參數處理常式設定成您自己的函式來改變。  如果您沒有在您指定的函式當中終止應用程式，控制權將還給接收到無效參數的函式，並且一般這些函式將會停止執行，回傳錯誤碼，並且將 `errno` 設置成錯誤碼。  在許多情況下， `errno` 值和回傳值都是 `EINVAL` ，表示無效的參數。  在某些情況下會回傳比較特定的錯誤碼，例如 `EBADF` 代表將錯誤的檔案指標做參數傳遞。  如需更多關於 errno 的資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 請參閱  
 [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)