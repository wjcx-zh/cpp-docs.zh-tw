---
title: "編譯器錯誤 C3715 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca60dcff0279982b01c70ee3c7603baf421bd434
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3715"></a>編譯器錯誤 C3715
'pointer': 必須是 'class' 的指標  
  
 指定在指標[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md) ，未指向有效的類別。 若要修正這個錯誤，請確認您`__hook`和`__unhook`呼叫指定有效的類別的指標。