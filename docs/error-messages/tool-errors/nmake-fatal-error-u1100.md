---
title: NMAKE 嚴重錯誤 U1100 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d4ed57c980813c8539fbffed0e41a35048c0571
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 嚴重錯誤 U1100
巨集 '巨集名稱' 是在批次規則 'rule' 的內容中不合法  
  
 當批次模式規則的命令區塊直接或間接參考不是 $< 的特殊檔案巨集時，NMAKE 就會產生此錯誤。  
  
 $< 是批次模式規則中唯一允許的巨集。