---
title: 連結器工具警告 LNK4037 |Microsoft 文件
ms.custom: ''
ms.date: 10/04/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b87f0a415d6ae7d282e29c2ca67fda043c2a901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302431"
---
# <a name="linker-tools-warning-lnk4037"></a>連結器工具警告 LNK4037

>'*符號*' 不存在; 已忽略

裝飾的名稱*符號*不可以使用排序[/](../../build/reference/order-put-functions-in-order.md)選項，因為在程式中找不到。 檢查的規格*符號*順序回應檔中。 如需詳細資訊，請參閱[/ORDER （依順序的 Put 函式）](../../build/reference/order-put-functions-in-order.md)連結器選項。

> [!NOTE]
> 連結的靜態函式無法排序，因為靜態函式名稱不是公用的符號名稱。 當 **/** 是指定為靜態順序回應檔中的每個符號會產生這個連結器警告或找不到。