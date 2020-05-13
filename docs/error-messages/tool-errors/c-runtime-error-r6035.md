---
title: C 執行階段錯誤 R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: ff3cd0259df92aa5cdade3f78a240e69f8f6f7de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377485"
---
# <a name="c-runtime-error-r6035"></a>C 執行階段錯誤 R6035

Microsoft Visual C++運行時庫,錯誤 R6035 - 此應用程式中的一個模組正在初始化模組的全域安全 Cookie,而依賴於該安全 Cookie 的函數處於活動狀態。  提前致電__security_init_cookie。

在首次使用全域安全 Cookie 之前,必須調用[__security_init_cookie。](../../c-runtime-library/reference/security-init-cookie.md)

全域安全 Cookie 用於使用[/GS (緩衝區安全檢查)](../../build/reference/gs-buffer-security-check.md)編譯的代碼和使用結構化異常處理的代碼中的緩衝區溢出保護。 基本上,在進入受溢出保護的函數時,將 Cookie 放在堆疊上,在退出時,堆疊上的值與全域 Cookie 進行比較。 它們之間的任何差異都表明發生了緩衝區溢出,導致程式立即終止。

錯誤 R6035 表示`__security_init_cookie`在輸入 受保護函數後對進行了調用。 如果繼續執行,將檢測到虛假緩衝區溢出,因為堆疊上的 Cookie 將不再與全域 Cookie 匹配。

請考慮以下 DLL 示例。 DLL 入口點透過連結器[/ENTRY(入口符號)](../../build/reference/entry-entry-point-symbol.md)選項設定為 DllEntryPoint。 這繞過了 CRT 的初始化,該初始化通常會初始化全域安全 Cookie,因此`__security_init_cookie`DLL 本身 必須呼叫 。

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

此示例將生成錯誤 R6035,因為 DllEntryPoint 使用結構化異常處理,因此使用安全 Cookie 檢測緩衝區溢出。 在調用 Dll 初始化時,全域安全 Cookie 已放在堆疊上。

此範例示範了正確的方法:

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

在這種情況下,DllEntryPoint 不受緩衝區溢出的保護(它沒有本地字串緩衝區,並且不使用結構化異常處理);因此,它可以安全地調用`__security_init_cookie`。 然後,它調用受保護的幫助器函數。

> [!NOTE]
> 錯誤消息 R6035 僅由 x86 調試 CRT 生成,僅用於結構化異常處理,但條件是所有平臺上的錯誤,以及所有形式的異常處理(如 C++ EH)。

## <a name="see-also"></a>另請參閱

[MSVC 中的安全性功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)
