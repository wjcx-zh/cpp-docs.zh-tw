---
title: 編譯器錯誤 C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 20c17eaa6555b5511ecbc930eacdb2ec92475b23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749499"
---
# <a name="compiler-error-c3893"></a>編譯器錯誤 C3893

' var '： initonly 資料成員的左值使用只允許用於類別 ' type_name ' 的實例構造函式

靜態[initonly](../../dotnet/initonly-cpp-cli.md)資料成員只能在靜態的函式中取得其位址。

實例（非靜態） initonly 資料成員只能在實例（非靜態）的函式中取得其位址。

下列範例會產生 C3893：

```cpp
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```
