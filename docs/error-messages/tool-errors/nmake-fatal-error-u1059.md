---
title: NMAKE 嚴重錯誤 U1059 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb038befdb7c587c6fe2a734003abba585c3e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 嚴重錯誤 U1059
語法錯誤: '}' 相依中遺漏  
  
 相依的搜尋路徑指定不正確。 可能是有空格之路徑的右括號中 (**}**) 已省略。  
  
 相依性的目錄規格的語法  
  
 **{**   
 ***目錄*} 相依**  
  
 其中`directories`指定一個或多個路徑，每個以分號分隔 (**;**)。 沒有空格。  
  
 如果以巨集取代部分或全部的搜尋路徑，確定巨集展開中存在不能有空格。