---
title: "推斷相依和規則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe7c49607f466d8fd1d333883414b24d7837432b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="inferred-dependents-and-rules"></a>推斷相依和規則
如果有適用的推斷規則，nmake 就會假設為目標的推斷的相依。 規則適用於：  
  
-   *toext*符合目標的擴充功能。  
  
-   *fromext*具有目標的基底名稱以及檔案的副檔名存在於目前或指定的目錄中的相符項目。  
  
-   *fromext*處於[。尾碼](../build/dot-directives.md); 沒有其他*fromext*在比對規則有較高**。尾碼**優先順序。  
  
-   沒有明確的相依具有較高**。尾碼**優先順序。  
  
 推斷相依項目可能會導致未預期的副作用。 如果目標的描述區塊包含命令，NMAKE 就會執行這些命令，而不是命令中的規則。  
  
## <a name="see-also"></a>請參閱  
 [推斷規則](../build/inference-rules.md)