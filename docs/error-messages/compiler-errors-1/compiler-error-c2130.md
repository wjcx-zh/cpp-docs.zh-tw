---
title: 編譯器錯誤 C2130
ms.date: 11/04/2016
f1_keywords:
- C2130
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
ms.openlocfilehash: aee0931926cad2ac30631c152aeb94bfd24befd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397597"
---
# <a name="compiler-error-c2130"></a>編譯器錯誤 C2130

\#列必須是字串，包含檔案名稱，找到 'token'

[#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 後面的選擇性檔名語彙基元必須是字串。

下列範例會產生 C2130：

```
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```