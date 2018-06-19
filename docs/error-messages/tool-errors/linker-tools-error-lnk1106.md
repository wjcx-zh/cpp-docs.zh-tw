---
title: 連結器工具錯誤 LNK1106 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3dedaa2bd500b11f06f9cfa98802fdd6ca84534
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298087"
---
# <a name="linker-tools-error-lnk1106"></a>連結器工具錯誤 LNK1106
無效的檔案或磁碟已滿： 無法搜尋到的位置  
  
 此工具無法讀取或寫入`location`記憶體對應檔案中。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  磁碟已滿。  
  
     釋放一些磁碟空間並重新連結。  
  
2.  嘗試透過網路連結。  
  
     某些網路不完全支援連結器所使用的記憶體對應檔案。 嘗試連結您的本機磁碟上。  
  
3.  不正確的磁碟區塊。  
  
     雖然的作業系統和磁碟硬體應該已偵測到這類錯誤，您可能想要執行磁碟檢查程式。  
  
4.  堆積空間不足。  
  
     請參閱[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)如需詳細資訊。