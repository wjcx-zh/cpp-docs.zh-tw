---
title: 編譯器警告 (層級 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: e9fcb4356d993d86b622fd49c4a75d587554f7c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388601"
---
# <a name="compiler-warning-level-1-c4055"></a>編譯器警告 (層級 1) C4055

> '*轉換*': 從資料指標'*type1*'到函式指標'*type2*'

## <a name="remarks"></a>備註

**已淘汰：** 藉由 Visual Studio 2017 和更新版本，不會產生這個警告。

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
