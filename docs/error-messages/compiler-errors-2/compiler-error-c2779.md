---
title: 編譯器錯誤 C2779
ms.date: 11/04/2016
f1_keywords:
- C2779
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
ms.openlocfilehash: cf2a59726e87f5cd2cdb82129db2677bf6a69d29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220232"
---
# <a name="compiler-error-c2779"></a>編譯器錯誤 C2779

' 宣告 '：屬性方法只能與非靜態資料成員相關聯

**`property`** 擴充屬性不正確地套用至靜態資料成員。

下列範例會產生 C2779：

```cpp
// C2779.cpp
struct A {
   static __declspec(property(put=PutProp))
   // try the following line instead
   __declspec(property(put=PutProp))
      int prop;   // C2779
   int PutProp(void);
};
```
