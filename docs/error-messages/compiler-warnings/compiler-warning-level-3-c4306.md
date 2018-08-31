---
title: 編譯器警告 （層級 3） C4306 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4306
dev_langs:
- C++
helpviewer_keywords:
- C4306
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab5372213819375a6c1fec3cfc43970415b6486a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219990"
---
# <a name="compiler-warning-level-3-c4306"></a>編譯器警告 (層級 3) C4306

> '*識別碼*': 從轉換'*type1*'to'*type2*' 更大的

識別項是型別轉換為較大的指標。 新的型別未填入高的位元會是零填滿。

這個警告可能表示非預期的轉換。 產生的指標可能無效。