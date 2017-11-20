---
title: "CRT 中的安全性功能 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
dev_langs: C++
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6dd54fcfc9612b5c20288b78b60d84257ab8f2f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="security-features-in-the-crt"></a>CRT 中的安全性功能
許多舊的 CRT 函式都有較新且更安全的版本。 如果存在較安全的函式，則較舊且較不安全的版本會被標示為已取代，而且新的版本會有 `_s` (「安全」) 後置詞。  
  
 在此內容中，「已取代」只是表示不建議使用該函式；它並沒有指出已排程將該函式從 CRT 移除。  
  
 安全的函式不會防止或修正安全性錯誤，而是會在錯誤發生時偵測到它們。 它們會針對錯誤狀況執行額外的檢查，並在發生錯誤時叫用錯誤處理常式 (請參閱[參數驗證](../c-runtime-library/parameter-validation.md))。  
  
 例如，`strcpy` 函式並無法判斷它正在複製的字串對於目的地緩衝區是否太大。 不過，其安全的對應版本 `strcpy_s` 會將緩衝區的大小作為參數，因此可以判斷是否會發生緩衝區溢位。 如果您使用 `strcpy_s` 將 11 個字元複製到 10 個字元的緩衝區，這是您本身所造成的錯誤；`strcpy_s` 並無法修正您的錯誤，但它可以偵測錯誤，並透過叫用無效的參數處理常式來通知您。  
  
## <a name="eliminating-deprecation-warnings"></a>排除取代警告  
 針對較舊且較不安全的函式，有幾種方式可以排除取代警告。 最簡單的是只需定義 `_CRT_SECURE_NO_WARNINGS` 或使用 [warning](../preprocessor/warning.md) pragma。 這兩種方式都會停用取代警告，不過然造成警告的安全性問題仍然會存在。 最好的方法是保持啟用取代警告，並利用新的 CRT 安全性功能。  
  
 在 C++ 中，最簡單的方式是使用[安全範本多載](../c-runtime-library/secure-template-overloads.md)，它在許多情況下，可以透過將針對已取代函式的呼叫取代為針對該函式新安全版本的呼叫，來排除取代警告。 例如，以這個針對 `strcpy` 的已取代呼叫為例：  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為 1，便可以透過將 `strcpy` 呼叫變更為 `strcpy_s` 來排除警告，並進一步防止緩衝區溢位。 如需詳細資訊，請參閱 [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md)。  
  
 對於那些沒有安全範本多載的已取代函式，您便應該考慮手動更新您的程式碼，以使用安全的版本。  
  
 另一個與安全性無關的已取代警告來源是 POSIX 函式。 使用 POSIX 函式的標準對等版本來取代 POSIX 函式名稱 (例如，將 [access](../c-runtime-library/reference/access-crt.md) 變更為 [_access](../c-runtime-library/reference/access-waccess.md))，或透過定義 `_CRT_NONSTDC_NO_WARNINGS` 來停用 POSIX 相關的取代警告。 如需詳細資訊，請參閱[已取代的 CRT 函式](http://msdn.microsoft.com/en-us/7e259932-c6c8-4c1a-9637-639e591681a5) \(英文\)。  
  
## <a name="additional-security-features"></a>其他的安全性功能  
 安全性功能包括下列各項：  
  
-   `Parameter Validation`. 在安全函式和許多現有的函式版本中，傳遞至 CRT 函式的參數會受到驗證。 這些驗證包括：  
  
    -   檢查傳遞至函式的 `NULL` 值。  
  
    -   檢查列舉值的有效性。  
  
    -   檢查整數值是否在有效範圍內。  
  
-   如需詳細資訊，請參閱[參數驗證](../c-runtime-library/parameter-validation.md)。  
  
-   無效參數的處理常式也可供開發人員存取。 遇到無效參數時，與其進行判斷提示並結束應用程式，CRT 提供使用 [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 函式檢查這些問題的方式。  
  
-   `Sized Buffers`. 安全函式要求將緩衝區大小傳遞給任何寫入緩衝區的函式。 安全版本會在寫入緩衝區之前驗證緩衝區是否夠大，以協助避免發生可能會允許惡意程式碼執行的危險緩衝區溢位錯誤。 這些函式通常傳回 `errno` 類型的錯誤碼，並在緩衝區大小太小的情況下叫用無效的參數處理常式。 讀取輸入緩衝區的函式 (例如 `gets`) 具有會要求您指定大小上限的安全版本。  
  
-   `Null termination`. 某些會留下潛在非終止字串的函式具有安全版本，可確保字串適當地以 null 結束。  
  
-   `Enhanced error reporting`. 安全函式所傳回的錯誤碼，將會包含比現有函式所提供的還要多的資訊。 安全函式和許多現有函式現在會設定 `errno`，且經常傳回 `errno` 程式碼類型，以提供更好的錯誤報告。  
  
-   `Filesystem security`. 安全的檔案 I/O API 支援預設案例中的安全檔案存取。  
  
-   `Windows security`. 安全的程序 API 會強制執行安全性原則，並允許指定 ACL。  
  
-   `Format string syntax checking`. 偵測到無效字串，例如在 `printf` 格式字串中使用不正確的類型欄位字元。  
  
## <a name="see-also"></a>另請參閱  
 [參數驗證](../c-runtime-library/parameter-validation.md)   
 [安全範本多載](../c-runtime-library/secure-template-overloads.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)