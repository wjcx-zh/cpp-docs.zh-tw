---
title: 安全範本多載 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
dev_langs:
- C++
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18f4d0962101e859ebab38ffaf333c0adae91548
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016673"
---
# <a name="secure-template-overloads"></a>安全範本多載

Microsoft 已取代許多 C 執行階段程式庫 (CRT) 函數，並改為使用能增強安全性的版本。 例如，使用較安全的 `strcpy_s` 來取代 `strcpy`。 已被取代的函數是安全性錯誤的常見來源，因為它們並無法防止能覆寫記憶體的作業。 根據預設，編譯器會在您使用這些函數時產生取代警告。 CRT 針對這些函數提供 C++ 範本多載，來讓使用者能更輕鬆地轉換至較安全的版本。

例如，此程式碼片段會產生警告，因為 `strcpy` 已被取代：

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

取代警告的目的是要讓您知道您的程式碼可能不安全。 如果您已確定程式碼無法覆寫記憶體，則會有幾個選擇。 您可以選擇忽略該警告、在 include 陳述式之前定義符號 `_CRT_SECURE_NO_WARNINGS` 來使 CRT 標頭隱藏警告，或是更新程式碼以使用 `strcpy_s`：

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

範本多載能提供其他選擇。 如果您將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為 1，會啟用標準 CRT 函數的範本多載以自動呼叫較安全的版本。 如果 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 為 1，您將不必對程式碼做出任何變更。 其幕後作業為將對 `strcpy` 的呼叫變更為對 `strcpy_s` 的呼叫，同時自動提供大小引數。

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

巨集 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 並不會影響採用計數的函數 (例如 `strncpy`)。 若要針對 Count 函數啟用範本多載，請將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 定義為 1。 不過，在這麼做之前，請確定您的程式碼是傳遞字元的計數，而非緩衝區的大小 (這是一個常見的錯誤)。 此外，在呼叫安全版本的情況下，於函數呼叫後在緩衝區末端明確寫入 null 結束字元的程式碼是不必要的。 如果您需要截斷行為，請參閱 [_TRUNCATE](../c-runtime-library/truncate.md)。

> [!NOTE]
>  巨集 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 也需要將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為 1。 如果 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 定義為 1，且 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為 0，應用程式將不會執行任何範本多載。

當您將 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 定義為 1 時，會啟用安全版本 (名稱結尾為 "_s") 的範本多載。 在此情況下，如果 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 為 1，便必須對原始程式碼做出一項小變更：

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

只有函數的名稱需要變更 (加入 "_s")，範本多載會負責提供大小引數。

根據預設，`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 和 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 會定義為 0 (已停用)，且 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 會定義為 1 (已啟用)。

請注意，這些範本多載僅適用於靜態陣列。 動態配置的緩衝區需要進行其他的原始程式碼變更。 讓我們重新造訪上述的範例：

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; you have to change it to
                       // strcpy_s(szBuf, 10, "test");
```

以及這個範例：

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>請參閱

[CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)<br/>
[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)