---
title: "連結器工具錯誤 LNK1106 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1106
dev_langs: C++
helpviewer_keywords: LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 793d788462a3a449c654c30ec874399a3bb85728
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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