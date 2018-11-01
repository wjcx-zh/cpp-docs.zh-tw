---
title: 編譯器錯誤 C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: dbb65628aa6e0da94a91a59724ca8e1cd5b56491
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620872"
---
# <a name="compiler-error-c3510"></a>編譯器錯誤 C3510

找不到相依類型程式庫 'type_lib'

[no_registry](../../preprocessor/no-registry.md)並[auto_search](../../preprocessor/auto-search.md)傳遞給`#import`但編譯器找不到參考的型別程式庫。

若要解決這個錯誤，請確定所有的型別程式庫和參考的型別程式庫會提供給編譯器。

下列範例會產生 C3510:

假設下列兩個型別程式庫所建置，且該 C3510a.tlb 已刪除或不在路徑上。

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

然後第二個型別程式庫原始程式碼：

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

然後用戶端程式碼：

```
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```