---
title: "推斷規則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 932aad860cd2b78208857ca7b028e35cd96d481e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="inference-rules"></a>推斷規則
推斷規則提供命令可以更新目標，並推斷目標的相依性。 推斷規則中的延伸符合單一目標，且具有相同的基底名稱的相依。 推斷規則是使用者定義或預先定義的。預先定義的規則可以重新定義。  
  
 如果過時的相依性沒有任何命令，而且如果[。尾碼](../build/dot-directives.md)包含相依項的擴充功能，NMAKE 會使用其延伸符合目標和現有的規則檔中的目前或指定的目錄。 如果多個規則符合現有檔案， **。尾碼**清單決定該使用哪種，則為清單的優先順序會向下延伸從左到右。 如果相依檔案不存在，而且未列示為另一個描述區塊中的目標，推斷規則可以建立遺漏相依從具有相同的基底名稱的另一個檔案。 如果描述區塊的目標有任何相依項目或命令，推斷規則可以更新目標。 推斷規則可以建置命令列的目標，即使描述區塊不存在。 NMAKE 可能叫用的推斷相依的規則，即使指定明確的相依性。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [定義規則](../build/defining-a-rule.md)  
  
 [批次模式規則](../build/batch-mode-rules.md)  
  
 [預先定義的規則](../build/predefined-rules.md)  
  
 [推斷的相依和規則](../build/inferred-dependents-and-rules.md)  
  
 [推斷規則的優先順序](../build/precedence-in-inference-rules.md)  
  
## <a name="see-also"></a>請參閱  
 [NMAKE 參考](../build/nmake-reference.md)