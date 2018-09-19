---
title: 編譯器警告 （層級 4） C4337 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4337
dev_langs:
- C++
helpviewer_keywords:
- C4337
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5b4e72f3dfda903a3d0f4563a730dc44411f79c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016451"
---
# <a name="compiler-warning-level-4-c4337"></a>編譯器警告 (層級 4) C4337

自動匯入交互參考的型別程式庫 'typelib1' 中 'typelib2'

Auto_search 屬性[#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)造成隱含匯入類型程式庫。

從下列兩個檔案 （編譯 midl.exe） 建立的磁碟上的指定兩個型別程式庫：

```
// C4337a.idl
[
  uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12B)
]
library C4337aLib
{
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12C)]
   enum E_C4337a
   {
      one = 0,
      two = 1,
      three = 2
    };
};
```

然後第二個.idl 檔案

```
// C4337b.idl
[
   uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12D)
]

library C4337bLib
{
   importlib("c4337a.tlb");

   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12E)]
   struct S_C4337b
   {
      enum E_C4337a e;
   };
};
```

下列範例會產生 C4337:

```
// C4337.cpp
// compile with: /W4 /LD
#import "c4337b.tlb" auto_search   // C4337
// explicitly #import all type libraries to resolve
// #import "C4337a.tlb"
// #import "C4337b.tlb"
```