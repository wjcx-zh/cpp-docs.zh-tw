---
title: 連結器工具錯誤 LNK2017 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095423b5f2d86cef309ed4316ff72d195b11eb26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313068"
---
# <a name="linker-tools-error-lnk2017"></a>連結器工具錯誤 LNK2017
'segment' /largeaddressaware: no 沒有無效的 'symbol' 重新配置  
  
 您嘗試建立具有 32 位元位址的 64 位元映像。 若要這樣做，您必須：  
  
-   使用固定的負載位址。  
  
-   限制 3 GB 映像。  
  
-   指定[/largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)。