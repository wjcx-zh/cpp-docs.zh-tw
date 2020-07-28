---
title: 編譯器錯誤 C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 5c11133fbf28cfb98de1367955c00c899e8b1042
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214525"
---
# <a name="compiler-error-c3646"></a>編譯器錯誤 C3646

> ' 規範 '：未知的覆寫規範

## <a name="remarks"></a>備註

編譯器在預期會尋找覆寫規範的位置找到標記，但編譯器無法辨識 token。

例如，如果 **_NOEXCEPT**無法辨識的*規範*，請將它取代為關鍵字 **`noexcept`** 。

如需詳細資訊，請參閱覆[寫](../../extensions/override-specifiers-cpp-component-extensions.md)規範。

## <a name="example"></a>範例

下列範例會產生 C3646，並顯示可修正此問題的方法：

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
