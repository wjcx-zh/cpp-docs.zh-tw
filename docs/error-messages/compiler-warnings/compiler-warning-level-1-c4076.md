---
title: 編譯器警告 (層級 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200251"
---
# <a name="compiler-warning-level-1-c4076"></a>編譯器警告 (層級 1) C4076

> '*type 修飾*詞 '：不能與類型 '*typename*' 搭配使用

## <a name="remarks"></a>備註

類型修飾詞（不論其是否為已**簽署**或**未簽署**）不能與非整數類型搭配使用。 已忽略*類型修飾*詞。

## <a name="example"></a>範例

下列範例會產生 C4076;若要修正此問題，請移除不**帶正負**號的類型修飾詞：

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
