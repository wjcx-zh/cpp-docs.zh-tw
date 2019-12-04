---
title: 編譯器錯誤 C2946
ms.date: 11/04/2016
f1_keywords:
- C2946
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
ms.openlocfilehash: c0ea10b3614e20e7f47c8f6632843544b4842751
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755365"
---
# <a name="compiler-error-c2946"></a>編譯器錯誤 C2946

明確具現化；'class' 不是樣板類別特製化

您無法明確具現化非樣板類別。

## <a name="example"></a>範例

下列範例會產生 C2946。

```cpp
// C2946.cpp
class C {};
template C;  // C2946
int main() {}
```
