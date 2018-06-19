---
title: 運算式評估工具錯誤 CXX0065 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78c25c9c6bde27219f10e4047dc7a6ab416f55d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297533"
---
# <a name="expression-evaluator-error-cxx0065"></a>運算式評估工具錯誤 CXX0065
變數必須有堆疊框架  
  
 運算式包含存在於目前的範圍內，但尚未尚未建立變數。  
  
 當您已逐步初構函式，但尚未設定函式之堆疊框架，或您已逐步函式的結束代碼，就會發生此錯誤。  
  
 逐步初構程式碼執行之前評估運算式之前已設定的堆疊框架。  
  
 這個錯誤是與 can0065 相同。