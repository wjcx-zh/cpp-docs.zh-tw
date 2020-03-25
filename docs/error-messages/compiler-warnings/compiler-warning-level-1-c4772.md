---
title: 編譯器警告 (層級 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 89156b2f29fd21160e6abddc3ecb21efaee6dde1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175126"
---
# <a name="compiler-warning-level-1-c4772"></a>編譯器警告 (層級 1) C4772

> \#匯入參考了遺漏類型程式庫中的類型;'*遺漏-類型*' 當做預留位置使用

已使用[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞參考類型程式庫。 不過，類型程式庫包含另一個未使用 `#import`參考的類型程式庫參考。 編譯器找不到這個其他 .tlb 檔案。

請注意，如果您使用[/i （其他 Include 目錄）](../../build/reference/i-additional-include-directories.md)編譯器選項來指定這些目錄，編譯器將不會在不同的目錄中找到類型程式庫。 如果您想要編譯器在不同的目錄中尋找類型程式庫，請將這些目錄加入 PATH 環境變數中。

根據預設，此警告會發出為錯誤。 無法使用/W0. 隱藏 C4772

## <a name="example"></a>範例

這是重現 C4772 所需的第一個類型程式庫。

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

這是重現 C4772 所需的第二種類型程式庫。

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

下列範例會產生 C4772：

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```
