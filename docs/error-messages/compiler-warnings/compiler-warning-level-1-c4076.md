---
title: 編譯器警告 (層級 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 1958aec4d6642188af1467ab4cab1ecf55c29165
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223313"
---
# <a name="compiler-warning-level-1-c4076"></a>編譯器警告 (層級 1) C4076

> '*type 修飾*詞 '：不能與類型 '*typename*' 搭配使用

## <a name="remarks"></a>備註

類型修飾詞（不論是否為 **`signed`** 或 **`unsigned`** ）不能與非整數類型搭配使用。 已忽略*類型修飾*詞。

## <a name="example"></a>範例

下列範例會產生 C4076;若要修正此問題，請移除 **`unsigned`** 類型修飾詞：

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
