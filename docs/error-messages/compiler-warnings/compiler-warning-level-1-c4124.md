---
title: 編譯器警告（層級1） C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 59860bef108a3cd3e8bbbc6ff0790e17dbdaa0d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214486"
---
# <a name="compiler-warning-level-1-c4124"></a>編譯器警告（層級1） C4124

具有堆疊檢查的 __fastcall 效率不佳

已 **`__fastcall`** 啟用堆疊檢查時使用關鍵字。

**`__fastcall`** 慣例會產生較快的程式碼，但堆疊檢查會導致較慢的程式碼。 使用時 **`__fastcall`** ，請使用**check_stack** pragma 或/Gs. 關閉堆疊檢查

只有在這些條件下宣告的第一個函式才會發出這個警告。
