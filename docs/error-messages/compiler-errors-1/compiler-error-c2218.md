---
title: 編譯器錯誤 C2218 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52c449381c6e8a7391706ed6097bc38576bc69fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041281"
---
# <a name="compiler-error-c2218"></a>編譯器錯誤 C2218

'__vectorcall' 無法搭配 '/arch:IA32' 使用

只有在包含 Streaming SIMD Extensions 2 (SSE2) (含) 以上版本的 x86 和 x64 處理器機器碼中才支援 `__vectorcall` 呼叫慣例。 如需詳細資訊，請參閱 < [__vectorcall](../../cpp/vectorcall.md)。

若要修正此錯誤，請將編譯器選項變更為以 SSE2、AVX 或 AVX2 指令集為目標。 如需詳細資訊，請參閱 [/arch (x86)](../../build/reference/arch-x86.md)。