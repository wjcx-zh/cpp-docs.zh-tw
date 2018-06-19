---
title: 推斷相依和規則 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aae09fd756e0eb4eab3031beb5b4cba8c4d35a40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368040"
---
# <a name="inferred-dependents-and-rules"></a>推斷相依和規則
如果有適用的推斷規則，nmake 就會假設為目標的推斷的相依。 規則適用於：  
  
-   *toext*符合目標的擴充功能。  
  
-   *fromext*具有目標的基底名稱以及檔案的副檔名存在於目前或指定的目錄中的相符項目。  
  
-   *fromext*處於[。尾碼](../build/dot-directives.md); 沒有其他*fromext*在比對規則有較高 **。尾碼**優先順序。  
  
-   沒有明確的相依具有較高 **。尾碼**優先順序。  
  
 推斷相依項目可能會導致未預期的副作用。 如果目標的描述區塊包含命令，NMAKE 就會執行這些命令，而不是命令中的規則。  
  
## <a name="see-also"></a>另請參閱  
 [推斷規則](../build/inference-rules.md)