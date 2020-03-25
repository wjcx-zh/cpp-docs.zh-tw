---
title: 編譯器警告（層級1） C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: dfc3a91b2dcb3ed1e8f4f4993edd67219a6bf1d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163841"
---
# <a name="compiler-warning-level-1-c4103"></a>編譯器警告（層級1） C4103

' filename '：在包含標頭之後，對齊已變更，可能是因為遺漏 #pragma pack （pop）

封裝會影響類別的版面配置，而且通常如果封裝在標頭檔中有變更，可能會有問題。

在結束標頭檔之前，請使用 #pragma [pack](../../preprocessor/pack.md)（pop）來解決這個警告。

下列範例會產生 C4103：

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

然後，

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
