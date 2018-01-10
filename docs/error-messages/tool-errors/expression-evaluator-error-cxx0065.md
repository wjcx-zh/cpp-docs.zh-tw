---
title: "運算式評估工具錯誤 CXX0065 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0065
dev_langs: C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db01baa10191df50c1f319bf8320263657088d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0065"></a>運算式評估工具錯誤 CXX0065
變數必須有堆疊框架  
  
 運算式包含存在於目前的範圍內，但尚未尚未建立變數。  
  
 當您已逐步初構函式，但尚未設定函式之堆疊框架，或您已逐步函式的結束代碼，就會發生此錯誤。  
  
 逐步初構程式碼執行之前評估運算式之前已設定的堆疊框架。  
  
 這個錯誤是與 can0065 相同。