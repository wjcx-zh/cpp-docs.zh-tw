---
title: 編譯器警告 (層級 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: ff4a9b3d78a108a45abb18c22049b104e630bf15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280239"
---
# <a name="compiler-warning-level-4-c4960"></a>編譯器警告 (層級 4) C4960

'function' 太大而無法分析

使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到函式大於 65,535 個指令的輸入模組。 這類大型函式不適用於特性指引最佳化。

若要解決這個警告，請減少函式的大小。