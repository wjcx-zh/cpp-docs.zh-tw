---
title: 資源編譯器錯誤 RC2151 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8349aa14de6aec96fa1b526cbcffbe79036f804d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2151"></a>資源編譯器錯誤 RC2151
無法重新使用字串常數  
  
 您要使用相同的值在兩次**STRINGTABLE**陳述式。 請確定您未混淆重疊的十進位和十六進位值。  
  
 在每個識別碼**STRINGTABLE**必須是唯一的。 最大效率使用連續的常數，以開始 16 的倍數。