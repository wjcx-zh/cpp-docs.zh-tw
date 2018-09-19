---
title: 編譯器錯誤 C3715 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63ae3486b4db21a3aa241d5ebdbbfa0cdc6806f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026552"
---
# <a name="compiler-error-c3715"></a>編譯器錯誤 C3715

'pointer': 必須是 'class' 的指標

指定中的指標[__hook](../../cpp/hook.md)或是[__unhook](../../cpp/unhook.md) ，並未指向有效的類別。 若要修正這個錯誤，請確認您`__hook`和`__unhook`呼叫指定有效的類別的指標。