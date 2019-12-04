---
title: 編譯器錯誤 C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: 3f9dea77b739aa59474e60cf852fff2577ab6ba9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753623"
---
# <a name="compiler-error-c3510"></a>編譯器錯誤 C3510

找不到相依類型程式庫 ' type_lib '

[no_registry](../../preprocessor/no-registry.md)和[auto_search](../../preprocessor/auto-search.md)已傳遞至 `#import`，但編譯器找不到參考的類型程式庫。

若要解決這個錯誤，請確定所有類型程式庫和參考的類型程式庫都可供編譯器使用。

下列範例會產生 C3510：

假設已建立下列兩個類型程式庫，而且 C3510a 已刪除或不在路徑上。

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

然後是第二個類型程式庫的原始程式碼：

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

然後用戶端程式代碼：

```cpp
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```
