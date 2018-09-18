---
title: 編譯器錯誤 C2835 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2835
dev_langs:
- C++
helpviewer_keywords:
- C2835
ms.assetid: 41c70630-983f-4da2-8342-513cf48b0519
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97da0796b6b7f40462f4d0594e640ee98aa6aa49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044163"
---
# <a name="compiler-error-c2835"></a>編譯器錯誤 C2835

使用者定義轉換 'type' 沒有使用型式參數

使用者定義型別轉換不能使用的型式參數。

下列範例會產生 C2835:

```
// C2835.cpp
class A {
public:
   char v_char;

   A() {
      v_char = 'A';
   };
   operator char(char a) {   // C2835
   // try the following line instead
   // operator char() {
      return v_char + 1;
   };
};

int main() {
   A a;
}
```