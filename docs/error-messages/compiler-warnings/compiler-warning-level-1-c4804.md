---
title: 編譯器警告 （層級 1） C4804 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd1d1659ad6c8716cebf37a99f234af7b41f5745
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094802"
---
# <a name="compiler-warning-level-1-c4804"></a>編譯器警告 (層級 1) C4804

'operation': 不安全的類型 'bool'，在作業中使用

當您使用時，這項警告是針對`bool`變數或值以預期的方式。 如果您使用的運算子，例如負值的一元運算子，例如，產生 C4804 (**-**) 或補充運算子 (`~`)。 編譯器會評估運算式。

## <a name="example"></a>範例

下列範例會產生 C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```