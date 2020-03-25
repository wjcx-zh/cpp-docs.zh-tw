---
title: 編譯器錯誤 C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: f76515d58f020b414e6b79a7737463af80bd2d07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200809"
---
# <a name="compiler-error-c3398"></a>編譯器錯誤 C3398

'operator' : 無法從 'function_signature' 轉換成 'function_pointer'。 來源運算式必須是函式符號

使用 [/clr](../../cpp/clrcall.md) 編譯時，如果未指定 **__clrcall**呼叫慣例，編譯器會為每個函式產生兩個進入點 (位址)：原生進入點和 Managed 進入點。

根據預設，編譯器會傳回原生進入點，但有些情況需要 Managed 進入點 (例如，將位址指派給 `__clrcall` 函式指標時)。 為了讓編譯器可靠地選擇指派中的 Managed 進入點，右邊必須是函式符號。
