---
title: 嚴重錯誤 C1054 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9daac4944c57dbf08fe0ebcbc95993a97838585
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1054"></a>嚴重錯誤 C1054
編譯器限制： 初始設定式巢狀太深  
  
 程式碼超出初始設定式 （10-15 層級，取決於正在初始化的類型的組合） 的巢狀限制。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  簡化以減少巢狀結構正在初始化的資料類型。  
  
2.  初始化個別陳述式中的變數宣告之後。