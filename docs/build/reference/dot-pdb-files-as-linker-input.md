---
title: ".做為連結器輸入 Pdb 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5acdc01a58cf0d501be5947cddf710d1b7c6d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pdb-files-as-linker-input"></a>.Pdb 檔做為連結器輸入
使用 /Zi 選項編譯的 (.obj) 檔案包含的程式資料庫 (PDB) 名稱的物件。 您未指定物件的 PDB 檔案名稱給連結器。連結會尋找 PDB，必要時使用內嵌的名稱。 這也適用於偵錯程式庫; 中所包含的物件可偵錯的程式庫 PDB 必須可供連同摘要庫，連結器。  
  
 連結也會使用 PDB 保留的.exe 或.dll 檔案的偵錯資訊。 程式的 PDB 是輸出檔與輸入的檔中，因為它重建程式時，連結會更新 PDB。  
  
## <a name="see-also"></a>請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)