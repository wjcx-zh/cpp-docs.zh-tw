---
title: 編譯器警告 （層級 4） C4336 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4336
dev_langs:
- C++
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce0bc5a8a3df26a330de55c331d46b1f0c1d692
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051162"
---
# <a name="compiler-warning-level-4-c4336"></a>編譯器警告 (層級 4) C4336

匯入交互參考的類型程式庫 'type_lib1'，匯入 'type_lib2' 之前

使用所參考的型別程式庫[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞。 不過，類型程式庫包含未參考與另一個型別程式庫的參考`#import`。 編譯器找不到此其他的.tlb 檔案。

從下列兩個檔案 （編譯 midl.exe） 建立的磁碟上的指定兩個型別程式庫：

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

第二個類型程式庫：

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

下列範例會產生 C4336:

```
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```