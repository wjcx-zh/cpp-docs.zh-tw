---
title: 編譯器警告 (層級 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542307"
---
# <a name="compiler-warning-level-4-c4611"></a>編譯器警告 (層級 4) C4611

'function' 和 c + + 物件解構間的互動是不可移植

在某些平台，包含的函式**攔截**可能不支援的解構時超出範圍的 c + + 物件語意。

若要避免非預期的行為，請避免使用**攔截**有建構函式和解構函式的函式中。

只會一次; 發出這個警告請參閱[pragma 警告](../../preprocessor/warning.md)。