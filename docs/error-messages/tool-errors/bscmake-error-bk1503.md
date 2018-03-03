---
title: "BSCMAKE 錯誤 BK1503 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86f2b6d282857409cdb1e1d49e04775e9886cde4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 錯誤 BK1503
無法寫入檔案 'filename' [: 原因]  
  
 BSCMAKE 結合成一個瀏覽器資料庫編譯期間所產生的.sbr 檔案。 如果產生的瀏覽器資料庫超過 64 MB，或輸入 (.sbr) 檔案的數目超過 4092，就會發出這項錯誤。  
  
 如果問題因為多個 4092.sbr 檔，您必須減少輸入檔的數目。 從 Visual studio，這可藉由[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)您整個專案，然後重新檢查檔案的檔案為基礎。  
  
 如果問題因.bsc 檔案大於 64 MB，減少做為輸入的.sbr 檔案數目會減少產生的.bsc 檔的大小。 此外，瀏覽資訊的數量可能會降低/e m （排除巨集展開符號）、 /El （排除區域變數） 和 /Es （排除系統檔案）。  
  
## <a name="see-also"></a>請參閱  
 [BSCMAKE 選項](../../build/reference/bscmake-options.md)