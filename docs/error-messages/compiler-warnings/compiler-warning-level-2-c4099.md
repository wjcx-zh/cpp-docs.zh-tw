---
title: 編譯器警告 （層級 2） C4099 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d7ffee02e8e5414a0e06cc4ba0da77a50c75f53
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110168"
---
# <a name="compiler-warning-level-2-c4099"></a>編譯器警告 (層級 2) C4099

'identifier': 第一次出現 使用 'objecttype1'，之後現在發現使用 'objecttype2' 的類型名稱

宣告為結構的物件定義為類別，或宣告為類別的物件定義為結構。 編譯器會使用在定義中指定的類型。

## <a name="example"></a>範例

下列範例會產生 C4099。

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```