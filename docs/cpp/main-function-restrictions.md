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
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 10fe82b0bb7ad700164b05ba466854db7716ba76
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
