---
title: 編譯器警告 （層級 4） C4710 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f6de17f7005db3834bfcfc93aff03f12f0293ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046091"
---
# <a name="compiler-warning-level-4-c4710"></a>編譯器警告 (層級 4) C4710

'function': 未內嵌函式

內嵌展開，我們選取了指定的函式，但編譯器未進行內嵌。

由編譯器決定進行內嵌。 **內嵌**關鍵字，例如**註冊**關鍵字，編譯器時，可做為提示。 編譯器會使用啟發學習法，以判斷是否應該內嵌特定函式的速度、 進行編譯時，加速程式碼，或者它應內嵌特定函式讓程式碼較小的空間進行編譯時。 編譯器只會內嵌非常小的函式的空間進行編譯時。

在某些情況下，編譯器不會內嵌特定函式機械的原因。 請參閱[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)取得一份編譯器可能不會內嵌函式的原因。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。