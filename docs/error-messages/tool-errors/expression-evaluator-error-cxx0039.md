---
title: 運算式評估工具錯誤 CXX0039 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8681d73d2889433516b205a47c500193bbeabdb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297764"
---
# <a name="expression-evaluator-error-cxx0039"></a>運算式評估工具錯誤 CXX0039
模稜兩可的符號  
  
 C 運算式評估工具無法判斷哪一個執行個體，若要在運算式中使用的符號。 符號，就會發生在繼承樹狀結構中的一次以上。  
  
 您必須使用範圍解析運算子 (`::`) 來明確指定要在運算式中使用的執行個體。  
  
 這個錯誤是與 can0039 相同。