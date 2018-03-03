---
title: "推斷相依 |Microsoft 文件"
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
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 410e52dd9ee9605f6e29b81491bda0f4883e1cf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="inferred-dependents"></a>推斷相依
推斷的相依衍生自推斷規則，並評估之前明確的相依性。 如果推斷的相依過時相對於它的目標，NMAKE 就會叫用命令區塊，相依性。 如果推斷的相依不存在，或對自身的相依性而言已過期，NMAKE 就會先更新推斷的相依。 如需推斷相依的詳細資訊，請參閱[推斷規則](../build/inference-rules.md)。  
  
## <a name="see-also"></a>請參閱  
 [相依性](../build/dependents.md)