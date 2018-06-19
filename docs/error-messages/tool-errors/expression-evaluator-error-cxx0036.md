---
title: 運算式評估工具錯誤 CXX0036 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e1bf3cda85d7b3d64d51279688a52cec5c0336
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301680"
---
# <a name="expression-evaluator-error-cxx0036"></a>運算式評估工具錯誤 CXX0036
內容錯誤 {...} 規格  
  
 可以由任何使用內容運算子中的幾個錯誤產生這則訊息 (**{}**)。  
  
-   內容運算子語法 (**{}**) 有不正確。  
  
     內容運算子語法如下：  
  
     {*函式*，*模組*，*dll*}*運算式*  
  
     這會指定內容*運算式*。 內容運算子有相同的優先順序和使用方式，型別轉換。  
  
     可以省略尾端逗號。 如果任何一個*函式*，*模組*，或*dll*包含常值的逗號，您必須將整個名稱括在括號中。  
  
-   函式名稱拼字不正確或不存在於指定的模組或動態連結程式庫。  
  
     因為 C 是區分大小寫的語言，*函式*必須在來源中定義指定在大小寫完全相符。  
  
-   找不到 DLL 的模組。  
  
     請檢查指定的模組或 DLL 的完整路徑名稱。  
  
 這個錯誤是與 can0036 相同。