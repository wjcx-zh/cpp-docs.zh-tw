---
title: main 函式限制 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5be2df6e152b26bcade1970b35ad33655e8e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="main-function-restrictions"></a>main 函式限制
數個限制**主要**不會套用到其他的 c + + 函式的函式。 **主要**函式：  
  
-   不能多載 (請參閱[函式多載](function-overloading.md))。  
  
-   不能宣告為**內嵌**。  
  
-   不能宣告為**靜態**。  
  
-   無法取得自己的位址。  
  
-   不能被呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)