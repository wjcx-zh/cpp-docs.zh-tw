---
title: "資源編譯器嚴重錯誤 RW1025 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 487968f8a1242dd4c36e4bbd9b4ede08a5ab4d95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rw1025"></a>資源編譯器嚴重錯誤 RW1025
堆積記憶體不足  
  
 檢查有常駐記憶體的軟體，可能會佔用太多空間。 若要找出您有多少記憶體使用 CHKDSK 程式。  
  
 如果您要建立大型的資源檔，請將資源指令碼分成兩個檔案。 建立兩個.res 檔案之後, 使用 MS-DOS 命令列聯結在一起：  
  
```  
copy first.res /b + second.res /b full.res  
```