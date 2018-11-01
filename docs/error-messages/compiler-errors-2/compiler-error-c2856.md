---
title: 編譯器錯誤 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499602"
---
# <a name="compiler-error-c2856"></a>編譯器錯誤 C2856

\#pragma hdrstop 不可以 #if 區塊內

`hdrstop` Pragma 不能放在條件式編譯區塊的主體內。

移動`#pragma hdrstop`陳述式不會包含在區域`#if/#endif`區塊。