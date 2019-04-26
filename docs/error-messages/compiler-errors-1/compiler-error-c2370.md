---
title: 編譯器錯誤 C2370
ms.date: 11/04/2016
f1_keywords:
- C2370
helpviewer_keywords:
- C2370
ms.assetid: 03403e8f-f393-47c4-bd25-5c1c7ea7d5cd
ms.openlocfilehash: 28c337a5cadfaeced39ee6ed73601338941029fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188035"
---
# <a name="compiler-error-c2370"></a>編譯器錯誤 C2370

'identifier': 重複定義；儲存類別不同

已使用不同的儲存類別宣告的識別項。

## <a name="example"></a>範例

下列範例會產生 C2370：

```
// C2370.cpp
// compile with: /Za /c
extern int i;
static int i;   // C2370
int i;   // OK
```

## <a name="example"></a>範例

下列範例會產生 C2370：

```
// C2370b.cpp
#define Thread __declspec( thread )
extern int tls_i;
int Thread tls_i;   // C2370 declaration and the definition differ
int tls_i;   // OK
```