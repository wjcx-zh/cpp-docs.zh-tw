---
title: 編譯器錯誤 C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 1909fb999dd0f60224029b726f773c11fa69ee40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347151"
---
# <a name="compiler-error-c2384"></a>編譯器錯誤 C2384

'member'：無法將 __declspec(thread) 套用至 Managed 或 WinRT 類別的成員

[執行緒](../../cpp/thread.md)`__declspec`修飾詞不能在成員的 managed 或 Windows 執行階段類別。

Managed 程式碼中的靜態執行緒區域儲存區僅可以使用於以靜態方式載入的 DLL — 在處理序啟動時 DLL 必須以靜態方式載入。 Windows 執行階段不支援執行緒區域儲存區。

下列範例會產生 C2384，並示範如何在 C++/CLI 程式碼中修正此問題：

```
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