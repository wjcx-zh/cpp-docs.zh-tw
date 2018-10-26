---
title: 運算式評估工具錯誤 CXX0036 |Microsoft Docs
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
ms.openlocfilehash: a94ed846d2d4ebda2e457ee772a9f8bf081d69d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077164"
---
# <a name="expression-evaluator-error-cxx0036"></a>運算式評估工具錯誤 CXX0036

不正確的內容 {...} 規格

此訊息可以產生的任何內容運算子的使用中的數個錯誤 (**{}**)。

- 內容運算子的語法 (**{}**) 有不正確。

   內容運算子的語法是：

     {*函式*，*模組*，*dll*}*運算式*

   這會指定的內容*運算式*。 內容運算子有相同的優先順序和使用方式，為型別轉換。

   可以省略尾端逗號。 如果任一*函式*，*模組*，或*dll*包含常值逗號，您必須括號括住整個名稱。

- 函式名稱拼字不正確，或不存在於指定的模組或動態連結程式庫。

   C 是區分大小寫的語言，因為*函式*必須指定中確切的案例中，因為它定義在來源中。

- 找不到 DLL 的模組。

   檢查指定的模組或 DLL 的完整路徑名稱。

此錯誤是與 can0036 相同。