---
title: 嚴重錯誤 C1305 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cb1cf19d0fc4152fbb458d684972bb5a4418f37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1305"></a>嚴重錯誤 C1305
分析資料庫 'pgd_file' 是針對不同的架構  
  
 針對另一個平台已傳遞至 /ltcg: pginstrument 作業所產生的.pgd 檔[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)可供 x86 和[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]平台。 不過，與 /ltcg: pginstrument 運算平台所產生的.pgd 檔無效，無法做為輸入至 /ltcg: pgoptimize 不同平台。  
  
 若要解決這個錯誤，只傳遞使用 /ltcg: pginstrument 至 /ltcg: pgoptimize 相同平台上建立的.pgd 檔。