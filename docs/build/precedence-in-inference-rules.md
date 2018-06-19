---
title: 推斷規則的優先順序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36d462d4222cbfc143dd7487d4cb6b1b8bb3ba3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368482"
---
# <a name="precedence-in-inference-rules"></a>推斷規則的優先順序
如果有多重定義推斷規則，NMAKE 就會使用最高優先順序的定義。 下列清單顯示的優先順序從最高到最低：  
  
1.  定義 makefile; 中的推斷規則更新的定義，其優先順序。  
  
2.  Tools.ini; 在定義推斷規則更新的定義，其優先順序。  
  
3.  預先定義的推斷規則。  
  
## <a name="see-also"></a>另請參閱  
 [推斷規則](../build/inference-rules.md)