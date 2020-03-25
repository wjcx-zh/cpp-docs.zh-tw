---
title: 編譯器警告（層級1） C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176308"
---
# <a name="compiler-warning-level-1-c4124"></a>編譯器警告（層級1） C4124

具有堆疊檢查的 __fastcall 效率不佳

在啟用堆疊檢查的情況下，使用了 `__fastcall` 關鍵字。

`__fastcall` 慣例會產生更快的程式碼，但堆疊檢查會導致較慢的程式碼。 使用 `__fastcall`時，請使用**check_stack** pragma 或/Gs. 關閉堆疊檢查

只有在這些條件下宣告的第一個函式才會發出這個警告。
