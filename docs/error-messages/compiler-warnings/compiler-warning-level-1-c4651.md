---
title: 編譯器警告 (層級 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393515"
---
# <a name="compiler-warning-level-1-c4651"></a>編譯器警告 (層級 1) C4651

[定義] 指定先行編譯標頭，但不適用於目前的編譯

指定定義時所產生先行編譯標頭，但不是在此編譯中。

定義將會生效內先行編譯標頭，而不是在程式碼的其餘部分。

如果先行編譯標頭不在建置 /DSYMBOL，編譯器會產生這個警告如果 /Yu 編譯沒有 /DSYMBOL。  /Yu 命令列中加入 /DSYMBOL 可以解決這個警告。