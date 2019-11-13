---
title: 編譯器警告（層級1） C4632
ms.date: 11/04/2016
f1_keywords:
- C4632
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
ms.openlocfilehash: 4a24e54b443707775375a2adf833748eae347ce8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052584"
---
# <a name="compiler-warning-level-1-c4632"></a>編譯器警告（層級1） C4632

XML 檔批註：檔案拒絕存取：原因

.Xdc 檔案的路徑（`file`）無效，且未建立 .xdc 檔案。

下列範例會產生 C4632：

```cpp
// C4632.cpp
// compile with: /clr /docv:\\falsedir /LD /W1
// C4632 expected

/// Text for class MyClass.
public ref class MyClass {};
```