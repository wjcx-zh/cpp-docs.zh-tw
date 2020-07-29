---
title: 編譯器錯誤 C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 97f3290ef8bcb6a91442effdbf84261c03545ce2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209522"
---
# <a name="compiler-error-c2218"></a>編譯器錯誤 C2218

> '__vectorcall' 無法搭配 '/arch:IA32' 使用

**`__vectorcall`** 只有在包含 Streaming SIMD Extensions 2 （SSE2）和更新版本的 x86 和 x64 處理器上，機器碼才支援呼叫慣例。 如需詳細資訊，請參閱 [`__vectorcall`](../../cpp/vectorcall.md)。

若要修正此錯誤，請將編譯器選項變更為以 SSE2、AVX 或 AVX2 指令集為目標。 如需詳細資訊，請參閱[ `/arch` （x86）](../../build/reference/arch-x86.md)。
