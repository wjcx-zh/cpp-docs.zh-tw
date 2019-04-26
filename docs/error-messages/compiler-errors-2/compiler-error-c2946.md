---
title: 編譯器錯誤 C2946
ms.date: 11/04/2016
f1_keywords:
- C2946
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
ms.openlocfilehash: 0f61d047fcd070f3deea662cd3bd193f8e133659
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187601"
---
# <a name="compiler-error-c2946"></a>編譯器錯誤 C2946

明確具現化；'class' 不是樣板類別特製化

您無法明確具現化非樣板類別。

## <a name="example"></a>範例

下列範例會產生 C2946。

```
// C2946.cpp
class C {};
template C;  // C2946
int main() {}
```