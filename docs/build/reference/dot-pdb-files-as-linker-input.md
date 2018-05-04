---
title: .做為連結器輸入 Pdb 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6707be955b5c4a332d1162f53b1cb854391a2ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="pdb-files-as-linker-input"></a>.Pdb 檔做為連結器輸入
使用 /Zi 選項編譯的 (.obj) 檔案包含的程式資料庫 (PDB) 名稱的物件。 您未指定物件的 PDB 檔案名稱給連結器。連結會尋找 PDB，必要時使用內嵌的名稱。 這也適用於偵錯程式庫; 中所包含的物件可偵錯的程式庫 PDB 必須可供連同摘要庫，連結器。  
  
 連結也會使用 PDB 保留的.exe 或.dll 檔案的偵錯資訊。 程式的 PDB 是輸出檔與輸入的檔中，因為它重建程式時，連結會更新 PDB。  
  
## <a name="see-also"></a>另請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)