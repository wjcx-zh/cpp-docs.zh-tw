---
title: "嚴重錯誤 C1305 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b32f9e7555ce905323fd6074d35f1876cd999edd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1305"></a>嚴重錯誤 C1305
分析資料庫 'pgd_file' 是針對不同的架構  
  
 針對另一個平台已傳遞至 /ltcg: pginstrument 作業所產生的.pgd 檔[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)可供 x86 和[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]平台。 不過，與 /ltcg: pginstrument 運算平台所產生的.pgd 檔無效，無法做為輸入至 /ltcg: pgoptimize 不同平台。  
  
 若要解決這個錯誤，只傳遞使用 /ltcg: pginstrument 至 /ltcg: pgoptimize 相同平台上建立的.pgd 檔。