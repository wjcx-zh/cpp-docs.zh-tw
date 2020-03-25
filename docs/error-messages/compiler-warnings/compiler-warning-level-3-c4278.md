---
title: 編譯器警告 (層級 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174228"
---
# <a name="compiler-warning-level-3-c4278"></a>編譯器警告 (層級 3) C4278

> '*identifier*'：類型程式庫 '*tlb*' 中的識別碼已經是宏;使用 ' rename ' 限定詞

使用[#import](../../preprocessor/hash-import-directive-cpp.md)時，您所匯入之 typelib 中的識別碼會嘗試宣告識別碼*識別碼*。 不過，這已經是有效的符號。

使用 `#import` **rename**屬性，將別名指派給類型程式庫中的符號。
