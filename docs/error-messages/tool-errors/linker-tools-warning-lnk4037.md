---
title: 連結器工具警告 LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410300"
---
# <a name="linker-tools-warning-lnk4037"></a>連結器工具警告 LNK4037

>'*符號*' 不存在; 已忽略

裝飾的名稱*符號*不可以使用排序[/order](../../build/reference/order-put-functions-in-order.md)選項，因為在程式中找不到。 檢查的規格*符號*順序回應檔中。 如需詳細資訊，請參閱 < [/ORDER （依順序置放函式）](../../build/reference/order-put-functions-in-order.md)連結器選項。

> [!NOTE]
> 連結的靜態函式無法排序，因為靜態函式名稱不是公用的符號名稱。 當 **/order**指定，這個連結器警告針對靜態順序回應檔中的每個符號產生或找不到。