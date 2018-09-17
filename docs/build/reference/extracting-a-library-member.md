---
title: 擷取程式庫成員 |Microsoft Docs
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
ms.openlocfilehash: 9207a77868b3257d09f0d9efe38e4765cb8f4906
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726514"
---
# <a name="extracting-a-library-member"></a>引出程式庫成員

您可以使用程式庫來建立物件 (.obj) 檔案，其中包含一份現有的程式庫的成員。 若要擷取的成員複本，請使用下列語法：

```
LIB library /EXTRACT:member /OUT:objectfile
```

此命令會建立稱為的.obj 檔案*objectfile* ，其中包含一份`member`的*程式庫*。 `member`名稱會區分大小寫。 您可以擷取單一命令中的只能有一個成員。 /OUT 選項是必要項沒有預設輸出名稱。 如果檔名*objectfile*已經存在於指定的目錄 (或目前的目錄，如果不指定的任何目錄，但*objectfile*)，擷取*objectfile*會取代現有的檔案。

## <a name="see-also"></a>另請參閱

[LIB 參考](../../build/reference/lib-reference.md)