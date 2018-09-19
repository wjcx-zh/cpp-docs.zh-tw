---
title: 編譯器警告 （層級 4） C4960 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed6ba083017c84cd6af05b917ff8417b0394d7c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085715"
---
# <a name="compiler-warning-level-4-c4960"></a>編譯器警告 (層級 4) C4960

'function' 太大而無法分析

使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到函式大於 65,535 個指令的輸入模組。 這類大型函式不適用於特性指引最佳化。

若要解決這個警告，請減少函式的大小。