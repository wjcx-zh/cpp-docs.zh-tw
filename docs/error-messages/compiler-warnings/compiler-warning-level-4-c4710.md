---
title: 編譯器警告 (層級 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c30b98204f447f4d9d0ab8d687602a361d909363
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218061"
---
# <a name="compiler-warning-level-4-c4710"></a>編譯器警告 (層級 4) C4710

' function '：未內嵌函式

已選取指定的函式來進行內嵌展開，但編譯器未執行內嵌功能。

內嵌是以編譯器的判斷來執行。 **`inline`** 關鍵字（例如 **`register`** 關鍵字）是用來做為編譯器的提示。 編譯器會使用啟發學習法來判斷是否應該內嵌特定函式，以便在編譯速度時加速程式碼，或者，如果應該內嵌特定函式，以便在針對空間編譯時讓程式碼變得更小。 編譯器只會在編譯空間時內嵌非常小的函式。

在某些情況下，編譯器不會針對機械原因內嵌特定函式。 如需編譯器不會內嵌函式的原因清單，請參閱[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) 。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。
