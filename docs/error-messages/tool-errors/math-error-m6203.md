---
title: "運算錯誤 M6203 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6203
dev_langs:
- C++
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f65e016a736113ea4bcb9e488e792daa673d00d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6203"></a>運算錯誤 M6203
'function': _OVERFLOW 錯誤  
  
 指定的函式的結果就是太大，無法呈現。  
  
 這個錯誤呼叫`_matherr`函式名稱、 其引數，與錯誤類型的函式。 您可以重新撰寫`_matherr`函式來自訂特定執行階段浮點數學錯誤的處理。