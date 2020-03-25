---
title: 連結器工具錯誤 LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194807"
---
# <a name="linker-tools-error-lnk2011"></a>連結器工具錯誤 LNK2011

未在中連結的先行編譯物件;映射可能無法執行

如果您使用先行編譯標頭檔，連結會要求必須在中連結所有使用先行編譯標頭建立的物件檔案。 如果您有用來產生先行編譯標頭檔以與其他原始程式檔搭配使用的原始程式檔，您現在必須包含與先行編譯標頭檔一起建立的物件檔案。

例如，如果您編譯一個名為 STUB .cpp 的檔案來建立先行編譯標頭檔以與其他原始程式檔搭配使用，您就必須與 STUB 連結，否則會出現這個錯誤。 在下列命令列中，第一行是用來建立先行編譯標頭檔，也就是搭配 PROG1 和第三行使用 PROG2 的一般 .pch。 檔案 STUB .cpp 僅包含 `#include` 行（與 PROG1 和 PROG2 中相同的 `#include` 行），而且只會用來產生先行編譯標頭檔。 在最後一行中，必須在中連結存根 .obj，以避免 LNK2011。

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
