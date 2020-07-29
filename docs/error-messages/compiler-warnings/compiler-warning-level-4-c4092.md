---
title: 編譯器警告（層級4） C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 675e6ccbc516734a405620aa74eaa04ff2f75087
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219985"
---
# <a name="compiler-warning-level-4-c4092"></a>編譯器警告（層級4） C4092

> sizeof 會傳回「不帶正負號的長」

運算子的運算元 **`sizeof`** 非常大，所以 **`sizeof`** 傳回 **`unsigned long`** 。 此警告會出現在 Microsoft extensions （ [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) ）底下。 在 ANSI 相容性（ **`/Za`** ）下，會改為截斷結果。
