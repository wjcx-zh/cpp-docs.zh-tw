---
title: 編譯器錯誤 C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 45a140d3fd5f510ee2434950ca3c4b47c0756d75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447225"
---
# <a name="compiler-error-c3893"></a>編譯器錯誤 C3893

'var': initonly 資料成員的左值使用只允許出現在類別 'type_name' 的執行個體建構函式

靜態[initonly](../../dotnet/initonly-cpp-cli.md)資料成員只能有靜態建構函式中取得其位址。

執行個體 （非靜態） initonly 資料成員只能在執行個體 （非靜態） 建構函式中取得其位址。

下列範例會產生 C3893:

```
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