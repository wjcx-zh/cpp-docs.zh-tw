---
title: 推斷相依 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86ed1a8fe6c97ae11af50f59cb639ef6fd7c1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367894"
---
# <a name="inferred-dependents"></a>推斷相依
推斷的相依衍生自推斷規則，並評估之前明確的相依性。 如果推斷的相依過時相對於它的目標，NMAKE 就會叫用命令區塊，相依性。 如果推斷的相依不存在，或對自身的相依性而言已過期，NMAKE 就會先更新推斷的相依。 如需推斷相依的詳細資訊，請參閱[推斷規則](../build/inference-rules.md)。  
  
## <a name="see-also"></a>另請參閱  
 [相依性](../build/dependents.md)