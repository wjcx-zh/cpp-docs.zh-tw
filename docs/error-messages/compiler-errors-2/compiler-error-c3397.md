---
title: 編譯器錯誤 C3397
ms.date: 11/04/2016
f1_keywords:
- C3397
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
ms.openlocfilehash: c6ca48eb53cf1c6d661a201fa8c4d2539669b9bf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777415"
---
# <a name="compiler-error-c3397"></a>編譯器錯誤 C3397

預設引數中不允許彙總初始設定

陣列宣告不正確。  請參閱[陣列](../../extensions/arrays-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3397。

```
// C3397.cpp
// compile with: /clr
// /clr /c
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397
void Func2(array<int> ^p = gcnew array<int> (3));   // OK

int main() {
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK
}
```