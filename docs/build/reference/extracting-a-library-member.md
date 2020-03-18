---
title: 引出程式庫成員
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439876"
---
# <a name="extracting-a-library-member"></a>引出程式庫成員

您可以使用 LIB 建立包含現有文件庫成員複本的物件（.obj）檔案。 若要解壓縮成員的複本，請使用下列語法：

```
LIB library /EXTRACT:member /OUT:objectfile
```

此命令會建立名為*objectfile*的 .obj 檔案，其中包含連結*庫*的 `member` 複本。 `member` 名稱會區分大小寫。 您只能在單一命令中解壓縮一個成員。 需要/OUT 選項;沒有預設的輸出名稱。 如果指定的目錄中已存在名為*objectfile*的檔案（或目前的目錄中，如果未使用*objectfile*指定任何目錄），則解壓縮的*objectfile*會取代現有的檔案。

## <a name="see-also"></a>另請參閱

[LIB 參考](lib-reference.md)
