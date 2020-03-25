---
title: 編譯器警告 (層級 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199564"
---
# <a name="compiler-warning-level-1-c4650"></a>編譯器警告 (層級 1) C4650

不在先行編譯標頭檔中的調試資訊;只有標頭中的全域符號才可使用

先行編譯標頭檔未使用 Microsoft 符號偵錯工具資訊進行編譯。

當連結時，產生的可執行檔或動態連結程式庫檔案將不會包含先行編譯標頭檔中所包含之本機符號的偵錯工具資訊。

藉由使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令列選項重新編譯先行編譯標頭檔，即可避免此警告。
