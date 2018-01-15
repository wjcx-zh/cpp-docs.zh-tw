---
title: "引出程式庫成員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Lib
dev_langs: C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38f45463bb76f858d1b88c059de57a4b8b86227e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="extracting-a-library-member"></a>引出程式庫成員
您可以使用程式庫來建立包含現有的程式庫之成員的複製目的檔 (.obj)。 若要擷取成員的複本，請使用下列語法：  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 此命令會建立名為.obj 檔案*/objectfile* ，其中包含一份`member`的*文件庫*。 `member`名稱會區分大小寫。 您可以擷取在單一命令中的只能有一個成員。 /OUT 選項是必要項;沒有預設輸出名稱。 如果檔案呼叫*/objectfile*已存在於指定的目錄 (或目前的目錄，如果您沒有目錄指定*/objectfile*)，解壓縮*/objectfile*會取代現有的檔案。  
  
## <a name="see-also"></a>請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)