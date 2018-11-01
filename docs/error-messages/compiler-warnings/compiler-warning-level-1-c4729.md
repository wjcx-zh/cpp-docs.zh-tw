---
title: 編譯器警告 (層級 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: f5f93cadd97eefe0d6c6da97be99ec5fd82ece24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574385"
---
# <a name="compiler-warning-level-1-c4729"></a>編譯器警告 (層級 1) C4729

依據 flow graph 產生的警告，發現函式太大

如果要編譯的函式太大，無法可靠地檢查將產生警告的情況，則會產生這個警告。 使用 [/Od](../../build/reference/od-disable-debug.md) 編譯器選項時，才會產生這個警告。

若要解決這個警告，請將函式分為較小的函式。