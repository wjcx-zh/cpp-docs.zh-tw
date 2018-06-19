---
title: 運算式評估工具錯誤 CXX0015 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 945dbda4759fa2989acb0411d1a3216a5e9a036c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297605"
---
# <a name="expression-evaluator-error-cxx0015"></a>運算式評估工具錯誤 CXX0015
運算式太複雜 （堆疊溢位）  
  
 輸入的運算式已太複雜或巢狀層數太多量 C 運算式評估工具的可用儲存體。  
  
 溢位，通常會發生因為太多擱置中的計算。  
  
 重新安排運算式，以便可以評估運算式的每個元件，會發現，而不必等候計算運算式的其他部分。  
  
 將運算式分割為多個命令。  
  
 這個錯誤是與 can0015 相同。