---
title: "-ALLOWISOLATION |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0295d73e51e28fbdd953d7d9a3a2ae5131c27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="allowisolation"></a>/ALLOWISOLATION
指定資訊清單查閱的行為。  
  
## <a name="syntax"></a>語法  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>備註  
 **/ALLOWISOLATION**導致作業系統查閱和載入資訊清單。  
  
 **/ALLOWISOLATION**是預設值。  
  
 **/ALLOWISOLATION:NO**表示會載入可執行檔，好像沒有資訊清單和原因[EDITBIN 參考](../../build/reference/editbin-reference.md)設定`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`選擇性標頭中的位元`DllCharacteristics`欄位。  
  
 可執行檔停用隔離時，Windows 載入器並不會試圖尋找新建立處理序的應用程式資訊清單。 新的處理序沒有預設的啟用內容，，即使可執行檔本身中的資訊清單，或如果沒有資訊清單具有名稱*可執行檔名稱*.exe.manifest。  
  
## <a name="see-also"></a>請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [/ALLOWISOLATION （資訊清單查閱）](../../build/reference/allowisolation-manifest-lookup.md)   
 [資訊清單檔案參考](http://msdn.microsoft.com/library/aa375632.aspx)