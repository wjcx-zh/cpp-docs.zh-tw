---
title: 編譯器錯誤 C3715 |Microsoft 文件
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
ms.openlocfilehash: 9412592ac177fb49f065975db469c9f77b98e8c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3715"></a>編譯器錯誤 C3715
'pointer': 必須是 'class' 的指標  
  
 指定在指標[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md) ，未指向有效的類別。 若要修正這個錯誤，請確認您`__hook`和`__unhook`呼叫指定有效的類別的指標。