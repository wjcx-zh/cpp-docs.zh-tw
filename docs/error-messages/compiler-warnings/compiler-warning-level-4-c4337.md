---
title: 編譯器警告 (層級 4) C4337
ms.date: 11/04/2016
f1_keywords:
- C4337
helpviewer_keywords:
- C4337
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
ms.openlocfilehash: 5080c600e37468d5c3617769ddb4596a31be47f0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991226"
---
# <a name="compiler-warning-level-4-c4337"></a>編譯器警告 (層級 4) C4337

已自動匯入 ' typelib2 ' 中的交互參考類型程式庫 ' typelib1 '

[#Import](../../preprocessor/hash-import-directive-cpp.md)指示詞的 auto_search 屬性會造成隱含地匯入類型程式庫。

從下列兩個檔案（以 midl 編譯）所建立的磁片上，指定了兩個類型程式庫：

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

然後是第二個 .idl 檔案，

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

下列範例會產生 C4337：

```cpp
// C4337.cpp
// compile with: /W4 /LD
#import "c4337b.tlb" auto_search   // C4337
// explicitly #import all type libraries to resolve
// #import "C4337a.tlb"
// #import "C4337b.tlb"
```
