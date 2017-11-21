---
title: "運算式評估工具錯誤 CXX0024 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0024
dev_langs: C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 386e04d8aa1655896b77f8492d7929778edd6109
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>運算式評估工具錯誤 CXX0024
作業需要左值  
  
 如需要左值的作業指定了不會評估為左值的運算式。  
  
 左值 （因此稱為因為它會出現在指派陳述式的左邊） 是指的記憶體位置的運算式。  
  
 例如，`buffer[count]`是有效的左值，因為它所指向的特定記憶體位置。 邏輯比較`zed != 0`不是有效的左值，因為其評估結果為 TRUE 或 FALSE，未為記憶體位址。  
  
 這個錯誤是與 can0024 相同。