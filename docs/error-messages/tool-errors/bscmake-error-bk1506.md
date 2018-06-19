---
title: BSCMAKE 錯誤 BK1506 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e19ec77818c8017387519b03e400c09d47021bc5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300419"
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 錯誤 BK1506
無法開啟檔案 'filename' [: 原因]  
  
 BSCMAKE 無法開啟檔案。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  另一個處理序鎖定的檔案。 如果`reason`指出**權限遭拒**，瀏覽器可能使用此檔案。 關閉 [瀏覽] 視窗，然後重試建置。  
  
2.  磁碟已滿。  
  
3.  硬體錯誤。  
  
4.  指定的輸出檔案具有相同名稱與現有的子目錄。