---
title: 編譯器錯誤 C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165034"
---
# <a name="compiler-error-c2870"></a>編譯器錯誤 C2870

'name': 命名空間定義必須出現在檔案範圍，或立即在另一個命名空間定義

定義命名空間`name`不正確。 命名空間必須定義在檔案範圍 （以外的所有區塊和類別） 或立即在另一個命名空間。

下列範例會產生 C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```