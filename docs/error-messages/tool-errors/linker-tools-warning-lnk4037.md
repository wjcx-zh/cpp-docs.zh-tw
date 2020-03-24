---
title: 連結器工具警告 LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 43fae7d0f19f96998d2e1a1739bc3e596bbd9ea9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194196"
---
# <a name="linker-tools-warning-lnk4037"></a>連結器工具警告 LNK4037

>'*symbol*' 不存在;忽略

裝飾名稱*符號*無法使用[/order](../../build/reference/order-put-functions-in-order.md)選項排序，因為它在程式中找不到。 請檢查訂單回應檔案中的*符號*規格。 如需詳細資訊，請參閱[/order （依序放置](../../build/reference/order-put-functions-in-order.md)函式）連結器選項。

> [!NOTE]
> 連結無法排序靜態函式，因為靜態函數名稱不是公用符號名稱。 指定 **/order**時，會針對訂單回應檔案中的每個符號（靜態或找不到）產生此連結器警告。
