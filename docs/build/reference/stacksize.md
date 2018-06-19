---
title: STACKSIZE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2093762b3c6f21d319c53a85da5ec5b430a1fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376243"
---
# <a name="stacksize"></a>STACKSIZE
設定堆疊的大小 (以位元組為單位)。  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## <a name="remarks"></a>備註  
 設定堆疊的對等方法是使用[堆疊配置](../../build/reference/stack-stack-allocations.md)（/ 堆疊） 選項。 請參閱該選項，如需詳細資訊的文件，關於*保留*和`commit`引數。  
  
 這個選項就在 Dll 上的沒有作用。  
  
## <a name="see-also"></a>另請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)