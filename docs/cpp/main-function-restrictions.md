---
title: "main 函式限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a94844a0d5636c58a764114ed6f413923d69950
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="main-function-restrictions"></a>main 函式限制
數個限制**主要**不會套用到其他的 c + + 函式的函式。 **主要**函式：  
  
-   不能多載 (請參閱[函式多載](function-overloading.md))。  
  
-   不能宣告為**內嵌**。  
  
-   不能宣告為**靜態**。  
  
-   無法取得自己的位址。  
  
-   不能被呼叫。  
  
## <a name="see-also"></a>請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)