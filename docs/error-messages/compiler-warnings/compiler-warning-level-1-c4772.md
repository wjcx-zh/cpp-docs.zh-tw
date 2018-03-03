---
title: "編譯器警告 （層級 1） C4772 |Microsoft 文件"
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C4772
dev_langs:
- C++
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 631cd4f872c7b8912b791417c04f6c6e9e056bdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4772"></a>編譯器警告 (層級 1) C4772

> \#匯入從遺漏的類型程式庫; 參考型別'*遺漏類型*' 做為預留位置

類型程式庫參考與[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞。 不過，類型程式庫包含未參考的另一個類型程式庫的參考`#import`。 編譯器找不到此.tlb 檔案。

請注意，編譯器會不到類型程式庫不同的目錄中是否您使用[（其他 Include 目錄） /I](../../build/reference/i-additional-include-directories.md)編譯器選項以指定這些目錄。 如果您想要在不同的目錄中尋找類型程式庫編譯器，將這些目錄加入至 PATH 環境變數。

依預設會發出這個警告視為錯誤。 無法隱藏 C4772 /W0 與。

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

這是重現 C4772 第二個型別程式庫。

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