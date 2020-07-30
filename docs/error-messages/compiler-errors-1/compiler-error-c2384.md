---
title: 編譯器錯誤 C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 321ccd23bc273f5fa548f75fd44bc320bcf4c426
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225510"
---
# <a name="compiler-error-c2384"></a>編譯器錯誤 C2384

'member'：無法將 __declspec(thread) 套用至 Managed 或 WinRT 類別的成員

[執行緒](../../cpp/thread.md) **`__declspec`** 修飾詞不能用在 managed 或 Windows 執行階段類別的成員上。

Managed 程式碼中的靜態執行緒區域儲存區僅可以使用於以靜態方式載入的 DLL — 在處理序啟動時 DLL 必須以靜態方式載入。 Windows 執行階段不支援執行緒區域儲存區。

下列範例會產生 C2384，並示範如何在 C++/CLI 程式碼中修正此問題：

```cpp
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```
