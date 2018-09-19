---
title: 編譯器錯誤 C2856 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2856
dev_langs:
- C++
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df6226bfd2fc11f05f894091f4ff02c145d09e11
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072705"
---
# <a name="compiler-error-c2856"></a>編譯器錯誤 C2856

\#pragma hdrstop 不可以 #if 區塊內

`hdrstop` Pragma 不能放在條件式編譯區塊的主體內。

移動`#pragma hdrstop`陳述式不會包含在區域`#if/#endif`區塊。