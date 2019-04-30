---
title: 編譯器警告 (層級 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 95243ab66d5d0296e1c316ff8dde7add75a030cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385455"
---
# <a name="compiler-warning-level-1-c4772"></a>編譯器警告 (層級 1) C4772

> \#匯入參考型別從遺漏的類型程式庫;'*遺漏類型*' 做為預留位置

使用所參考的型別程式庫[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞。 不過，類型程式庫包含未參考與另一個型別程式庫的參考`#import`。 編譯器找不到此其他的.tlb 檔案。

請注意，編譯器會不到類型程式庫中不同的目錄是否您使用[/I （其他 Include 目錄）](../../build/reference/i-additional-include-directories.md)編譯器選項以指定這些目錄。 如果您想要編譯器尋找不同的目錄中的類型程式庫，請將這些目錄加入 PATH 環境變數。

依預設會發出這個警告視為錯誤。 無法隱藏 C4772 /W0 使用。

## <a name="example"></a>範例

這是重現 C4772 的第一個類型程式庫。

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

這是重現 C4772 的第二個類型程式庫。

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

下列範例會產生 C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```