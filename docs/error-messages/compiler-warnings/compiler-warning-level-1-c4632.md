---
title: 編譯器警告 (層級 1) C4632
ms.date: 11/04/2016
f1_keywords:
- C4632
helpviewer_keywords:
- C4632
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
ms.openlocfilehash: f1870da4f7889d79f5a4eabfcc3a95a21703e9fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393541"
---
# <a name="compiler-warning-level-1-c4632"></a>編譯器警告 (層級 1) C4632

XML 文件註解： 檔案-拒絕存取： 原因

.Xdc 檔的路徑 (`file`) 無效，並不建立任何.xdc 檔案。

下列範例會產生 C4632:

```
// C4632.cpp
// compile with: /clr /docv:\\falsedir /LD /W1
// C4632 expected

/// Text for class MyClass.
public ref class MyClass {};
```