---
title: 編譯器錯誤 C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 7e148ced19e34a57172e3d606c6efdb2f5d012d6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740451"
---
# <a name="compiler-error-c2041"></a>編譯器錯誤 C2041

基底 ' number ' 的數位 ' character ' 不合法

指定的字元不是基底的有效數字（例如八進位或十六進位）。

下列範例會產生 C2041：

```cpp
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

可能的解決方案：

```cpp
// C2041b.cpp
// compile with: /c
int j = 071;
```
