---
title: "NMAKE 嚴重錯誤 U1059 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1059
dev_langs: C++
helpviewer_keywords: U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70b1546068678c811f6123d3c8059dfd6d914f4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 嚴重錯誤 U1059
語法錯誤: '}' 相依中遺漏  
  
 相依的搜尋路徑指定不正確。 可能是有空格之路徑的右括號中 (**}**) 已省略。  
  
 相依性的目錄規格的語法  
  
 **{**   
 ***目錄*} 相依**  
  
 其中`directories`指定一個或多個路徑，每個以分號分隔 (**;**)。 沒有空格。  
  
 如果以巨集取代部分或全部的搜尋路徑，確定巨集展開中存在不能有空格。