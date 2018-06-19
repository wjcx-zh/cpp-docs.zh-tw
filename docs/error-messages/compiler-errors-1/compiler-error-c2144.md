---
title: 編譯器錯誤 C2144 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2144
dev_langs:
- C++
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60a6b0a6019ab6ddf1a403d2cbd4f6ef96b2a865
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171140"
---
# <a name="compiler-error-c2144"></a>編譯器錯誤 C2144

> 語法錯誤: '*類型*'前面必須有'*語彙基元*'

編譯器預期*語彙基元*找到*類型*改為。

這個錯誤可能被因遺漏右大括號、 右括號或分號。

當您嘗試從包含泛空白字元的 CLR 關鍵字建立巨集時，也會發生 C2144。

如果您嘗試進行類型轉送，您也可以參閱 C2144。 請參閱[類型轉送 (C + + /CLI)](../../windows/type-forwarding-cpp-cli.md)如需詳細資訊。

## <a name="examples"></a>範例

下列範例會產生 C2144，並示範如何修正此問題：

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

下列範例會產生 C2144，並示範如何修正此問題：

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```