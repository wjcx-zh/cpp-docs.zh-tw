---
title: BSCMAKE 錯誤 BK1517 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6f5619a7c2a6ccf671845b27bbedf93d8eb2d69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-error-bk1517"></a>BSCMAKE 錯誤 BK1517
sbrfile 以 /Yc 和 /Yu 編譯原始程式檔  
  
 .Sbr 檔案參照了自己。 它可能已使用 /Yc 編譯之後重新編譯使用 /Yu。 /Yc，重設原始程式檔的編譯器選項，然後選取 **重建**以產生新的.sbr 檔案。 不重新編譯 /Yu 的原始程式檔。