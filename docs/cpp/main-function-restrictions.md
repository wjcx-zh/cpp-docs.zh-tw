---
title: main 函式限制 |Microsoft Docs
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
ms.openlocfilehash: 981d4c8c0ef30993811e5dbb6fd0a112a6447011
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406490"
---
# <a name="main-function-restrictions"></a>main 函式限制
數個限制**主要**並不適用於任何其他 c + + 函式的函式。 **主要**函式：  
  
-   無法多載 (請參閱[函式多載](function-overloading.md))。  
  
-   不可以宣告為**內嵌**。  
  
-   不可以宣告為**靜態**。  
  
-   無法取得自己的位址。  
  
-   不能被呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)