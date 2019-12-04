---
title: 編譯器錯誤 C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743519"
---
# <a name="compiler-error-c2480"></a>編譯器錯誤 C2480

' identifier '： ' thread ' 僅適用于靜態範圍的資料項目

您無法使用 `thread` 屬性搭配自動變數、非靜態資料成員、函數參數，或函式宣告或定義。

僅針對全域變數、靜態資料成員和本機靜態變數使用 `thread` 屬性。

下列範例會產生 C2480：

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
