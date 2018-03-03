---
title: "NMAKE 嚴重錯誤 U1073 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: faae317df44560991a88d47ec7f123e6a8126429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 嚴重錯誤 U1073
不知道如何使 'targetname'  
  
 指定的目標不存在，並沒有任何要執行的命令或套用的推斷規則。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  請檢查目標名稱的拼字。  
  
2.  如果*targetname*是虛擬目標，其指定為目標，以在另一個描述區塊。  
  
3.  如果*targetname*是巨集引動過程中，確定它不會展開為 null 字串。