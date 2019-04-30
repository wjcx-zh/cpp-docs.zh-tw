---
title: C 執行階段錯誤 R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: cbade3ce8686c8c293b8d40a73c546805e42215d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399976"
---
# <a name="c-runtime-error-r6035"></a>C 執行階段錯誤 R6035

Microsoft VisualC++執行階段程式庫、 錯誤 R6035-此應用程式中的模組正在初始化模組的全域安全性 cookie 依賴該安全性 cookie 的函式作用中時。  呼叫 __security_init_cookie 稍早所示。

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)全域安全性 cookie 第一次使用之前必須先呼叫。

全域安全性 cookie 用於在編譯的程式碼中的緩衝區滿溢保護[/GS （緩衝區安全性檢查）](../../build/reference/gs-buffer-security-check.md)和程式碼中使用結構化例外狀況處理。 基本上，在進入滿溢保護的函式，此 cookie 會放在堆疊上，並結束時，在堆疊上的值比較通用的 cookie。 它們之間的任何差異表示已發生緩衝區溢位，而導致程式立即終止。

錯誤 R6035 表示呼叫`__security_init_cookie`之後輸入的受保護的函式進行。 如果要繼續執行，因為在堆疊上的 cookie 就不再符合全域 cookie 會會偵測到假性的緩衝區滿溢。

請考慮下列範例中，DLL。 DLL 進入點，會透過連結器設定為： DllEntryPoint [/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)選項。 這會略過 CRT 初始化會因此必須呼叫該 DLL 本身，則通常會初始化全域安全性 cookie， `__security_init_cookie`。

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

此範例會產生錯誤 R6035，因為： DllEntryPoint 使用結構化例外狀況處理，因此會使用安全性 cookie 偵測緩衝區溢位。 DllInitialize 呼叫時，全域安全性 cookie 已經原本就設有堆疊上。

在此範例中示範的正確方式：

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

在此情況下，： DllEntryPoint 不會受到保護的緩衝區滿溢 （它有沒有本機字串緩衝區，但未使用結構化例外狀況處理）;因此可以安全地呼叫`__security_init_cookie`。 接著，它會呼叫受保護的 helper 函式。

> [!NOTE]
>  R6035 是錯誤訊息只由 x86 產生偵錯 CRT，並只會針對結構化例外狀況處理，但條件所有平台，而且可用於所有形式的例外狀況的錯誤處理，例如C++EH。

## <a name="see-also"></a>另請參閱

[在 MSVC 中的安全性功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)