---
title: "CRT 中的安全性功能 | Microsoft Docs"
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
  - "_CRT_SECURE_NO_DEPRECATE"
  - "_CRT_NONSTDC_NO_WARNINGS"
  - "_CRT_SECURE_NO_WARNINGS"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CRT_NONSTDC_NO_DEPRECATE"
  - "_CRT_NONSTDC_NO_WARNINGS"
  - "_CRT_SECURE_NO_DEPRECATE"
  - "_CRT_SECURE_NO_WARNINGS"
  - "緩衝區滿溢"
  - "緩衝區 [C++], 緩衝區滿溢"
  - "CRT, 安全性增強"
  - "CRT_NONSTDC_NO_DEPRECATE"
  - "CRT_NONSTDC_NO_WARNINGS"
  - "CRT_SECURE_NO_DEPRECATE"
  - "CRT_SECURE_NO_WARNINGS"
  - "已被取代警告 (安全性相關)"
  - "已被取代警告 (安全性相關), 停用"
  - "參數 [C++], 驗證"
  - "安全性 [CRT]"
  - "安全性已被取代警告 [C++]"
  - "安全性增強 CRT"
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CRT 中的安全性功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多舊 CRT 函式有更新，更安全的版本。  如果存在安全函式，將標記較舊，較不安全版本為被取代，而新版會包含 `_s` \(安全\) 尾碼。  
  
 在此內容中， 「被取代」表示不建議使用函式;它不表示函式從 CRT 中移除。  
  
 安全函式無法防止或改正安全性錯誤;而是發生時，它們會攔截錯誤。  他們會執行其他檢查錯誤條件，在錯誤的情況下，它們叫用錯誤處理常式 \(請參閱 [參數驗證](../c-runtime-library/parameter-validation.md)\)。  
  
 例如， `strcpy` 函式無法通知複製的字串是否大於緩衝區。  不過，它對應的安全函數， `strcpy_s`，會接受緩衝區的大小做為參數，因此，它可以判斷緩衝區滿溢 \(Buffer Overrun\) 是否會發生。  如果您使用 `strcpy_s` 複製十一個字元到十字元的緩衝區，這是您的錯誤; `strcpy_s` 無法修正您的錯誤，不過，它可以偵測到的錯誤並將叫用無效的參數處理常式通知您。  
  
## 排除取代警告  
 有幾個方式排除較舊，較不安全的函式物件的警告。  最簡單的方法是定義 `_CRT_SECURE_NO_WARNINGS` 或使用 [warning](../preprocessor/warning.md) Pragma。  任一個將會停用取代警告，但是會造成警告的安全性問題仍然存在。  保留警告啟用和利用新的 CRT 安全性功能是最好的。  
  
 在 C\+\+ 中，最簡單的方式是使用 [安全範本多載](../c-runtime-library/secure-template-overloads.md)，在許多情況下將透過從呼叫取代函式改為呼叫函式的新安全版本的方式排除物件警告。  例如，請考慮這個已取代的呼叫 `strcpy`:  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 定義 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 為 1 以藉由變更 `strcpy` 呼叫為防止緩衝區滿溢的 `strcpy_s` 來排除警告。  如需詳細資訊，請參閱[安全範本多載](../c-runtime-library/secure-template-overloads.md)。  
  
 如果是那些沒有安全範本多載的取代函式，您應該特別考慮手動更新您的程式碼以使用安全版本。  
  
 針對無關安全性警告的其他來源，是 POSIX 函式。  以標準對等用法取代 POSIX 函式名稱 \(例如，將 [access](../c-runtime-library/reference/access-crt.md) 變更為 [\_access](../c-runtime-library/reference/access-waccess.md)\)，或是定義 `_CRT_NONSTDC_NO_WARNINGS` 以停用 POSIX 相關物件的警告。  如需詳細資訊，請參閱[Deprecated CRT Functions](http://msdn.microsoft.com/zh-tw/7e259932-c6c8-4c1a-9637-639e591681a5)。  
  
## 其他安全性功能  
 以下是部分安全功能：  
  
-   `Parameter Validation`.  於安全函式和許多函式的預先存在版本，傳遞至 CRT 函式的參數會經過驗證。  這些驗證包括:  
  
    -   檢查傳遞至函式的 `NULL` 值。  
  
    -   檢查列舉值是否有效。  
  
    -   檢查整數值是否在有效範圍。  
  
-   如需詳細資訊，請參閱[參數驗證](../c-runtime-library/parameter-validation.md)。  
  
-   無效的參數處理常式也開放給開發人員存取。  當遇到無效的參數，代替判斷提示和關閉應用程式， CRT 提供檢查這些問題的函式 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。  
  
-   `Sized Buffers`.  安全函式需要緩衝區大小傳遞至所有對緩衝區寫入的函式。  安全版本於寫進它之前驗證緩衝區大小是否足夠，協助避免可能讓惡意程式碼執行的危險緩衝區超限執行階段錯誤。  如果緩衝區太小，這些函式通常會傳回 `errno` 型別的錯誤碼並叫用無效的參數處理常式。  從輸入緩衝區讀取的函數，例如 `gets`，存在需要指定最大值的安全版本。  
  
-   `Null termination`.  可能留下未結束字串的某些函式的安全版本會保證字串為 null 結尾。  
  
-   `Enhanced error reporting`.  安全函式傳回比之前版本的函式的錯誤碼更多詳細錯誤資訊。  安全函式和許多預先存在的函式現在會設定 `errno` 且通常會傳回 `errno` 型別，以提供更好的錯誤報告。  
  
-   `Filesystem security`.  安全檔案 I\/O API 於預設案例支援安全檔案存取。  
  
-   `Windows security`.  安全處理 API 強制執行安全性原則並允許 ACL 指定。  
  
-   `Format string syntax checking`.  無效的字串會被偵測到，例如，用於 `printf` 格式字串的無效型別字元。  
  
## 請參閱  
 [參數驗證](../c-runtime-library/parameter-validation.md)   
 [安全範本多載](../c-runtime-library/secure-template-overloads.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)