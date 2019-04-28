---
title: 編譯器警告 （層級 1） C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 04732619571420e777244b81bf4b93b775477a20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310977"
---
# <a name="compiler-warning-level-1-c4124"></a>編譯器警告 （層級 1） C4124

__fastcall 與堆疊檢查是效率不佳

`__fastcall`關鍵字已使用與堆疊檢查已啟用。

`__fastcall`慣例產生更快的程式碼，但堆疊檢查會導致較慢的程式碼。 使用時`__fastcall`，關閉使用中檢查堆疊**check_stack** pragma 或 /Gs。

只會針對這些情況下宣告的第一個函式，會發出這個警告。