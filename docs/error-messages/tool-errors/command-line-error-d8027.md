---
title: 命令列錯誤 D8027 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc93edb939001a1e1bed5d3f7a4113e8483e81dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-error-d8027"></a>命令列錯誤 D8027
無法執行 '元件'  
  
 指定的編譯器元件或連結器，編譯器無法執行。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  記憶體不足，無法載入元件。 如果 NMAKE 叫用編譯器執行外部 makefile 編譯器。  
  
2.  目前的作業系統無法執行此元件。 請確定路徑點的可執行檔的檔案適用於您的作業系統。  
  
3.  元件已損毀。 重新複製元件的安裝磁片，使用安裝程式。  
  
4.  選項指定不正確。 例如:   
  
    ```  
    cl /B1 file1.c  
    ```