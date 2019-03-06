---
title: 引出程式庫成員
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 4d7629707d99130551401fdda39a972ab2447480
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412883"
---
# <a name="extracting-a-library-member"></a>引出程式庫成員

您可以使用程式庫來建立物件 (.obj) 檔案，其中包含一份現有的程式庫的成員。 若要擷取的成員複本，請使用下列語法：

```
LIB library /EXTRACT:member /OUT:objectfile
```

此命令會建立稱為的.obj 檔案*objectfile* ，其中包含一份`member`的*程式庫*。 `member`名稱會區分大小寫。 您可以擷取單一命令中的只能有一個成員。 /OUT 選項是必要項沒有預設輸出名稱。 如果檔名*objectfile*已經存在於指定的目錄 (或目前的目錄，如果不指定的任何目錄，但*objectfile*)，擷取*objectfile*會取代現有的檔案。

## <a name="see-also"></a>另請參閱

[LIB 參考](../../build/reference/lib-reference.md)
