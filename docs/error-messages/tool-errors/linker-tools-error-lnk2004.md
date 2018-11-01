---
title: 連結器工具錯誤 LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 37eb01b5dd8266bce34e1a932271d5d9a9d15c52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529320"
---
# <a name="linker-tools-error-lnk2004"></a>連結器工具錯誤 LNK2004

gp 相對修復溢位，而 'target';short 區段 'section' 是太大，或超出範圍。

區段是太大。

若要解決這個錯誤，縮小短的區段，明確地將資料放在透過 #pragma 區段 （".sectionname"，讀取、 寫入、 長時間） 很長的區段，並使用`__declspec(allocate(".sectionname"))`有關資料定義和宣告。  例如，套用至物件的

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

您也可以移動以邏輯方式分組的資料到其本身會大於 8 個位元組，編譯器將 long 資料區段中配置的資料集合的結構。  例如，套用至物件的

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };

```

此錯誤後面是嚴重錯誤`LNK1165`。