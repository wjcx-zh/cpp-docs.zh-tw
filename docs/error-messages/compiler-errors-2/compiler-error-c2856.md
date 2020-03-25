---
title: 編譯器錯誤 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: c88610607083ecfaf5f20cd585b479991fa51b44
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201870"
---
# <a name="compiler-error-c2856"></a>編譯器錯誤 C2856

\#pragma hdrstop 不能在 #if 區塊內

`hdrstop` pragma 不能放在條件式編譯區塊的主體內。

將 `#pragma hdrstop` 語句移至未包含在 `#if/#endif` 區塊中的區域。
