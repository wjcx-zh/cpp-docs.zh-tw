---
title: 連結器工具錯誤 LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 0d26ab12c5b82d52b7dcbb176d9bfa033d7ddfee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194833"
---
# <a name="linker-tools-error-lnk2004"></a>連結器工具錯誤 LNK2004

' target ' 的 gp 相對修復溢位簡短區段 ' section ' 太大或超出範圍。

區段太大。

若要解決這個錯誤，請減少簡短區段的大小，方法是透過 #pragma 區段（". sectionname"、讀取、寫入、long）明確地將資料放入長區段中，並在資料定義和宣告上使用 `__declspec(allocate(".sectionname"))`。  例如，

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

您也可以將邏輯群組的資料移到它自己的結構中，這將會是大於8個位元組的資料集合，而編譯器會在長資料區段中配置。  例如，

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

此錯誤後面接著嚴重錯誤 `LNK1165`。
