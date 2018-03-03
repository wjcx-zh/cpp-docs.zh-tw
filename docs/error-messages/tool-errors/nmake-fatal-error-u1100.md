---
title: "NMAKE 嚴重錯誤 U1100 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7c4a42e47a29775bb53fdc0fd2f25c7bdc252f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 嚴重錯誤 U1100
巨集 '巨集名稱' 是在批次規則 'rule' 的內容中不合法  
  
 當批次模式規則的命令區塊直接或間接參考不是 $< 的特殊檔案巨集時，NMAKE 就會產生此錯誤。  
  
 $< 是批次模式規則中唯一允許的巨集。