---
title: 編譯器警告 (層級 1) C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: 1156bbfbed7aed9524b24b046b9ce9acdbdc8b8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300202"
---
# <a name="compiler-warning-level-1-c4109"></a>編譯器警告 (層級 1) C4109

未預期的識別項 'identifier'

會忽略包含未預期識別項的 pragma。

## <a name="example"></a>範例

```
// C4109.cpp
// compile with: /W1 /LD
#pragma init_seg( abc ) // C4109
```