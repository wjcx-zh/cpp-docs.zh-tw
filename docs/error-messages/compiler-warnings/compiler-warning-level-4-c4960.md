---
title: 編譯器警告 (層級 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198116"
---
# <a name="compiler-warning-level-4-c4960"></a>編譯器警告 (層級 4) C4960

'function' 太大而無法分析

使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到函式大於 65,535 個指令的輸入模組。 這類大型函式不適用於特性指引最佳化。

若要解決這個警告，請減少函式的大小。
