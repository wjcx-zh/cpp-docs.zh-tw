---
title: "連結器工具錯誤 LNK2017 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2017
dev_langs: C++
helpviewer_keywords: LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9446cb72ba9380e57b014b32d9ae00f6e9e554d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2017"></a>連結器工具錯誤 LNK2017
'segment' /largeaddressaware: no 沒有無效的 'symbol' 重新配置  
  
 您嘗試建立具有 32 位元位址的 64 位元映像。 若要這樣做，您必須：  
  
-   使用固定的負載位址。  
  
-   限制 3 GB 映像。  
  
-   指定[/largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)。