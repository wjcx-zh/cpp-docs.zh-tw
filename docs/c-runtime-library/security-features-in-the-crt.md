---
title: CRT 中的安全性功能
description: Microsoft C 執行時間中的安全 CRT 函式總覽。
ms.date: 09/29/2020
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
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
ms.openlocfilehash: 963f5510350aa3be25586811889189d28a5f7b66
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589883"
---
# <a name="security-features-in-the-crt"></a>CRT 中的安全性功能

許多舊的 CRT 函式都有較新且更安全的版本。 如果存在較安全的函式，則較舊且較不安全的版本會被標示為已取代，而且新的版本會有 `_s` (「安全」) 後置詞。

在此內容中，「已淘汰」表示不建議使用函數。 這並不表示函式已排程要從 CRT 移除。

安全的函式不會防止或更正安全性錯誤。 相反地，它們會在錯誤發生時加以攔截。 它們會針對錯誤狀況進行額外的檢查。 如果發生錯誤，則會叫用錯誤處理常式 (請參閱 [參數驗證](../c-runtime-library/parameter-validation.md)) 。

例如， `strcpy` 函數無法分辨它複製的字串是否太大而無法用於目的緩衝區。 它的安全對應 `strcpy_s` 項，會將緩衝區的大小視為參數。 因此它可以判斷是否會發生緩衝區溢位。 如果您使用將 `strcpy_s` 11 個字元複製到10個字元的緩衝區中，這在您的部分是錯誤的， `strcpy_s` 無法更正錯誤。 但是，它可以偵測您的錯誤，並叫用不正確參數處理常式來通知您。

## <a name="eliminating-deprecation-warnings"></a>排除取代警告

針對較舊且較不安全的函式，有幾種方式可以排除取代警告。 最簡單的是只需定義 `_CRT_SECURE_NO_WARNINGS` 或使用 [warning](../preprocessor/warning.md) pragma。 可能會停用取代警告，但造成警告的安全性問題仍然存在。 最好是讓取代警告保持啟用狀態，並利用新的 CRT 安全性功能。

在 c + + 中，最簡單的方法是使用 [安全範本](../c-runtime-library/secure-template-overloads.md)多載。 在許多情況下，這會排除取代的警告，方法是將對已被取代函式的呼叫取代為這些函數的安全版本呼叫。 例如，以這個針對 `strcpy` 的已取代呼叫為例：

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為 1，便可以透過將 `strcpy` 呼叫變更為 `strcpy_s` 來排除警告，並進一步防止緩衝區溢位。 如需詳細資訊，請參閱[安全範本多載](../c-runtime-library/secure-template-overloads.md)。

對於那些沒有安全範本多載的已取代函式，您便應該考慮手動更新您的程式碼，以使用安全的版本。

另一個與安全性無關的已取代警告來源是 POSIX 函式。 使用 POSIX 函式的標準對等版本來取代 POSIX 函式名稱 (例如，將 [access](../c-runtime-library/reference/access-crt.md) 變更為 [_access](../c-runtime-library/reference/access-waccess.md))，或透過定義 `_CRT_NONSTDC_NO_WARNINGS` 來停用 POSIX 相關的取代警告。 如需詳細資訊，請參閱[相容性](compatibility.md)。

## <a name="additional-security-features"></a>其他的安全性功能

某些安全性功能包括：

- `Parameter Validation`. 安全的函式以及許多不安全的對應專案都會驗證參數。 驗證可能包括：

  - 檢查是否有 **Null** 值。
  - 檢查列舉值的有效性。
  - 檢查整數值是否在有效範圍內。

- 如需詳細資訊，請參閱[參數驗證](../c-runtime-library/parameter-validation.md)。

- 無效參數的處理常式也可供開發人員存取。 當函數遇到不正確參數時，CRT 可讓您透過 [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)來檢查這些問題，而不是判斷提示並結束應用程式。

- `Sized Buffers`. 您必須將緩衝區大小傳遞給寫入緩衝區的任何安全函式。 安全版本會在寫入緩衝區之前，先驗證緩衝區夠大。 這有助於避免可能導致惡意程式碼執行的危險緩衝區溢位錯誤。 `errno`如果緩衝區的大小太小，這些函數通常會傳回錯誤碼，並叫用不正確參數處理常式。 讀取輸入緩衝區的函式 (例如 `gets`) 具有會要求您指定大小上限的安全版本。

- `Null termination`. 某些遺留潛在非終止字串的函式具有安全版本，可確保字串正確地以 null 終止。

- `Enhanced error reporting`. 安全的函式會傳回錯誤碼，而這些錯誤資訊比預先存在的函式所提供的更多。 安全函式和許多預先存在的函式現在已設定， `errno` 而且通常也會傳回程序 `errno` 代碼類型，以提供更好的錯誤報表。

- `Filesystem security`. 安全的檔案 I/O API 支援預設案例中的安全檔案存取。

- `Windows security`. 安全的程序 API 會強制執行安全性原則，並允許指定 ACL。

- `Format string syntax checking`. 偵測到無效字串，例如在 `printf` 格式字串中使用不正確的類型欄位字元。

## <a name="see-also"></a>另請參閱

[參數驗證](../c-runtime-library/parameter-validation.md)<br/>
[安全範本多載](../c-runtime-library/secure-template-overloads.md)<br/>
[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
