---
title: "推斷規則的優先順序 |Microsoft 文件"
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
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d22db9de1fc1941798c73c3c1c05a8ccd8571525
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="precedence-in-inference-rules"></a>推斷規則的優先順序
如果有多重定義推斷規則，NMAKE 就會使用最高優先順序的定義。 下列清單顯示的優先順序從最高到最低：  
  
1.  定義 makefile; 中的推斷規則更新的定義，其優先順序。  
  
2.  Tools.ini; 在定義推斷規則更新的定義，其優先順序。  
  
3.  預先定義的推斷規則。  
  
## <a name="see-also"></a>另請參閱  
 [推斷規則](../build/inference-rules.md)