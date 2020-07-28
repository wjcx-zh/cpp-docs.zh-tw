---
title: 編譯器警告 (層級 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 2ce261b36344126d541a9b453c88f7f8289ecba0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214330"
---
# <a name="compiler-warning-level-4-c4611"></a>編譯器警告 (層級 4) C4611

' function ' 和 c + + 物件銷毀之間的互動是不可移植的

在某些平臺上，包含的函式在 **`catch`** 超出範圍時可能不支援 c + + 物件的析構函數。

為避免非預期的行為，請避免 **`catch`** 在具有函式和析構函數的函式中使用。

這個警告只會發出一次;請參閱[pragma warning](../../preprocessor/warning.md)。
