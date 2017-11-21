---
title: "BSCMAKE 錯誤 BK1513 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1513
dev_langs: C++
helpviewer_keywords: BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3111d6823ed439aa9b26aead84c76de6bc403f9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE 錯誤 BK1513
非累加式更新需要所有 .SBR 檔案  
  
 BSCMAKE 無法建置新的瀏覽資訊 (.bsc) 檔，因為一個或多個 .sbr 檔遭到截斷。 若要尋找的已截斷的.sbr 檔案名稱，請參閱[BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)伴隨此錯誤的警告。  
  
 BSCMAKE 可以將 .bsc 檔更新為遭截斷的 .sbr 檔，但無法建置新的 .bsc 檔。 BSCMAKE 可能會因為下列原因而建置新的 .bsc 檔：  
  
-   .bsc 檔遺失。  
  
-   指定給 .bsc 檔的檔案名稱錯誤。  
  
-   .bsc 檔損毀。  
  
 若要解決這個問題，請刪除被截斷的 .sbr 檔並重新建置，或清除方案並重建。 (在 IDE 中，選擇 **建置**，**清除方案**，然後選擇 **建置**，**重建方案**。)