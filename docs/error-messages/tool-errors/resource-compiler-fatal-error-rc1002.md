---
title: 資源編譯器嚴重錯誤 RC1002 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1002
dev_langs:
- C++
helpviewer_keywords:
- RC1002
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 886b44d0a51df10295428daa69c8ea358660fd25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1002"></a>資源編譯器嚴重錯誤 RC1002
堆積空間不足  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  增加 Windows 交換檔空間。 如需有關如何增加分頁檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體。  
  
2.  將目前的檔案分割成較小的檔案，然後分別進行編譯。  
  
3.  移除其他程式或系統上執行的驅動程式。