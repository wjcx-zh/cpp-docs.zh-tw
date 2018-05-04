---
title: 引出程式庫成員 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc0dc67a6d9e4a3ff61aa3b82ac10b9eabcb94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="extracting-a-library-member"></a>引出程式庫成員
您可以使用程式庫來建立包含現有的程式庫之成員的複製目的檔 (.obj)。 若要擷取成員的複本，請使用下列語法：  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 此命令會建立名為.obj 檔案 */objectfile* ，其中包含一份`member`的*文件庫*。 `member`名稱會區分大小寫。 您可以擷取在單一命令中的只能有一個成員。 /OUT 選項是必要項;沒有預設輸出名稱。 如果檔案呼叫 */objectfile*已存在於指定的目錄 (或目前的目錄，如果您沒有目錄指定 */objectfile*)，解壓縮 */objectfile*會取代現有的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)