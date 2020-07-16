---
title: C 執行階段錯誤 R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: 9b92b1e2e123201d4f50422754b77f62b2ec943b
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404394"
---
# <a name="c-runtime-error-r6035"></a>C 執行階段錯誤 R6035

Microsoft Visual C++ 執行時間程式庫，錯誤 R6035-此應用程式中的模組會初始化模組的全域安全性 cookie，而依賴該安全性 cookie 的函式會在作用中。  呼叫稍早的 __security_init_cookie。

在第一次使用全域安全性 cookie 之前，必須先呼叫[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) 。

全域安全性 cookie 用於以[/gs （緩衝區安全性檢查）](../../build/reference/gs-buffer-security-check.md)編譯的程式碼，以及使用結構化例外狀況處理的程式碼中的緩衝區溢位保護。 基本上，在進入受超限保護的函式時，cookie 會放在堆疊上，而在結束時，會將堆疊上的值與全域 cookie 進行比較。 兩者之間的差異表示已發生緩衝區溢位，並導致程式立即終止。

錯誤 R6035 表示在 `__security_init_cookie` 輸入受保護的函式之後發出的呼叫。 如果繼續執行，則會偵測到假的緩衝區溢位，因為堆疊上的 cookie 不會再符合全域 cookie。

請考慮下列 DLL 範例。 DLL 進入點會透過連結器[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)選項設定為 DllEntryPoint。 這會略過 CRT 的初始化，這通常會初始化全域安全性 cookie，因此 DLL 本身必須呼叫 `__security_init_cookie` 。

```
// Wrong way to call __security_init_cookie
DllEntryPoint(...) {
   DllInitialize();
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}

void DllInitialize() {
   __security_init_cookie();
}
```

這個範例會產生錯誤 R6035，因為 DllEntryPoint 使用結構化例外狀況處理，因此會使用安全性 cookie 來偵測緩衝區溢位。 呼叫 DllInitialize 時，全域安全性 cookie 已放在堆疊上。

在此範例中，會示範正確的方式：

```
// Correct way to call __security_init_cookie
DllEntryPoint(...) {
   __security_init_cookie();
   DllEntryHelper();
}

void DllEntryHelper() {
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}
```

在此情況下，DllEntryPoint 不會受到緩衝區溢位的保護（它沒有本機字串緩衝區，也不會使用結構化例外狀況處理）。因此，它可以安全地呼叫 `__security_init_cookie` 。 然後，它會呼叫受保護的 helper 函式。

> [!NOTE]
> 錯誤訊息 R6035 只會由 x86 debug CRT 產生，而且僅適用于結構化例外狀況處理，但條件是所有平臺上的錯誤，以及所有形式的例外狀況處理，例如 c + + EH。

## <a name="see-also"></a>另請參閱

[MSVC 中的安全性功能](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/)
