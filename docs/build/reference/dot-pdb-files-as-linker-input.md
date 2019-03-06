---
title: .Pdb 檔做為連結器輸入
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: a29f01e5e5b30be4f7a983652d476a4512d2bec0
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426414"
---
# <a name="pdb-files-as-linker-input"></a>.Pdb 檔做為連結器輸入

使用了 /Zi 選項編譯的 (.obj) 檔案包含的程式資料庫 (PDB) 名稱的物件。 您未指定物件的 PDB 檔案名稱，連結器連結會尋找 PDB，必要時使用內嵌的名稱。 這也適用於可偵錯程式庫; 中所包含的物件可偵錯的程式庫 PDB 必須可供連同摘要庫，連結器。

連結也會用來保留的.exe 或.dll 檔案的偵錯資訊的 PDB。 程式的 PDB 是輸出檔和輸入的檔案，，因為它重建程式時，LINK 會更新 PDB。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](../../build/reference/link-input-files.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
