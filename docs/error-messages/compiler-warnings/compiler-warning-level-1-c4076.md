---
title: 編譯器警告 (層級 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437020"
---
# <a name="compiler-warning-level-1-c4076"></a>編譯器警告 (層級 1) C4076

> '*型別修飾詞*': 不可以搭配類型'*typename*'

## <a name="remarks"></a>備註

型別修飾詞，它是否**簽署**或是**不帶正負號**，不能與非整數類型。 *類型修飾詞*會被忽略。

## <a name="example"></a>範例

下列範例會產生 C4076;若要修正此問題，請移除**不帶正負號**型別修飾詞：

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```