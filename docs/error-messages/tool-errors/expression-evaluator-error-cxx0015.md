---
title: "運算式評估工具錯誤 CXX0015 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6f671b39fcc0027fdad5308192c5cbd8b8973717
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0015"></a>運算式評估工具錯誤 CXX0015
運算式太複雜 （堆疊溢位）  
  
 輸入的運算式已太複雜或巢狀層數太多量 C 運算式評估工具的可用儲存體。  
  
 溢位，通常會發生因為太多擱置中的計算。  
  
 重新安排運算式，以便可以評估運算式的每個元件，會發現，而不必等候計算運算式的其他部分。  
  
 將運算式分割為多個命令。  
  
 這個錯誤是與 can0015 相同。