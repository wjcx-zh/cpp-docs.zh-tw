---
title: "連結器工具警告 LNK4037 |Microsoft 文件"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4037
dev_langs: C++
helpviewer_keywords: LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c93eab2faf81e4cd743eae4befa2f842c100589
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4037"></a>連結器工具警告 LNK4037

>'*符號*' 不存在; 已忽略

裝飾的名稱*符號*不可以使用排序[/](../../build/reference/order-put-functions-in-order.md)選項，因為在程式中找不到。 檢查的規格*符號*順序回應檔中。 如需詳細資訊，請參閱[/ORDER （依順序的 Put 函式）](../../build/reference/order-put-functions-in-order.md)連結器選項。

> [!NOTE]
> 連結的靜態函式無法排序，因為靜態函式名稱不是公用的符號名稱。 當**/**是指定為靜態順序回應檔中的每個符號會產生這個連結器警告或找不到。