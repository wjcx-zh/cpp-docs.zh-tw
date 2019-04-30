---
title: 編譯器錯誤 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406843"
---
# <a name="compiler-error-c2856"></a>編譯器錯誤 C2856

\#pragma hdrstop 不可以 #if 區塊內

`hdrstop` Pragma 不能放在條件式編譯區塊的主體內。

移動`#pragma hdrstop`陳述式不會包含在區域`#if/#endif`區塊。