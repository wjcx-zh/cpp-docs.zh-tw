---
title: 編譯器警告 （層級 4） C4611 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 723976dc8b7085ede9b3157445ff3026de6fc4b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091045"
---
# <a name="compiler-warning-level-4-c4611"></a>編譯器警告 (層級 4) C4611

'function' 和 c + + 物件解構間的互動是不可移植

在某些平台，包含的函式**攔截**可能不支援的解構時超出範圍的 c + + 物件語意。

若要避免非預期的行為，請避免使用**攔截**有建構函式和解構函式的函式中。

只會一次; 發出這個警告請參閱[pragma 警告](../../preprocessor/warning.md)。