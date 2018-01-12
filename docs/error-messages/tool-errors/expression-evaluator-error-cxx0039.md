---
title: "運算式評估工具錯誤 CXX0039 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0039
dev_langs: C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6edef73f821030f8e8163c10b66efb64649e002f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0039"></a>運算式評估工具錯誤 CXX0039
模稜兩可的符號  
  
 C 運算式評估工具無法判斷哪一個執行個體，若要在運算式中使用的符號。 符號，就會發生在繼承樹狀結構中的一次以上。  
  
 您必須使用範圍解析運算子 (`::`) 來明確指定要在運算式中使用的執行個體。  
  
 這個錯誤是與 can0039 相同。