---
title: 編譯器錯誤 C3893 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 857d13de61f03bf0784d8cd10ad092d16f7acdaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087034"
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