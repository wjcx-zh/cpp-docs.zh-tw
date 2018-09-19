---
title: 編譯器警告 （層級 1） C4076 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f0a8066b8e79b75f3d5ede37f4e5ad6b61db168
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037875"
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