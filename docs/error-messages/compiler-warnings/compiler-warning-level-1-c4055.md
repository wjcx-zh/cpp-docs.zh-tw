---
title: 編譯器警告 （層級 1） C4052 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- C4055
dev_langs:
- C++
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29b1c8bcc836e35f7b8b81954ef247527d8ec35e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="compiler-warning-level-1-c4055"></a>編譯器警告 (層級 1) C4055

> '*轉換*': 從資料指標'*type1*'到函式指標'*type2*'

## <a name="remarks"></a>備註

**過時：**由 Visual Studio 2017 和更新版本的版本不會產生這個警告。

資料指標轉型 (可能不正確) 成函式指標。 這在 /Za 下是層級 1 警告，在 /Ze 下是層級 4 警告。

## <a name="example"></a>範例

下列範例會產生 C4055：

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

這在 /Ze 下是層級 4 警告。

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
