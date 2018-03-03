---
title: "運算錯誤 M6202 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 70a9496a2466ee36fed6d9c16194eef3516147f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6202"></a>運算錯誤 M6202
'function': 錯誤  
  
 指定的函式的引數為異常值，這個函式。 此函式未定義該引數。  
  
 這個錯誤呼叫`_matherr`函式名稱、 其引數，與錯誤類型的函式。 您可以重新撰寫`_matherr`函式來自訂特定執行階段浮點數學錯誤的處理。