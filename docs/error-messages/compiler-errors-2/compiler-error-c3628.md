---
title: 編譯器錯誤 C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 581aae7e1f979b3dd39caf2ce3d263fdb856c56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221681"
---
# <a name="compiler-error-c3628"></a>編譯器錯誤 C3628

'base class': managed 或 WinRTclasses 僅支援公用繼承

嘗試使用 managed 或 WinRT 類別做為[私人](../../cpp/private-cpp.md)或是[保護](../../cpp/protected-cpp.md)基底類別。 Managed 或 WinRT 類別只可用來當做基底類別具有[公開](../../cpp/public-cpp.md)存取。

下列範例會產生 C3628，並顯示如何修正此問題：

```
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
