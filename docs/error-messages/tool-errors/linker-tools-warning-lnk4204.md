---
title: 連結器工具警告 LNK4204 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f000fa42357a299c943eda0cd5f8697aee138f4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300588"
---
# <a name="linker-tools-warning-lnk4204"></a>連結器工具警告 LNK4204
'filename' 遺漏參考模組的偵錯資訊如同沒有偵錯資訊般連結物件  
  
 .Pdb 檔案有錯誤的簽章。 連結器將會繼續連結沒有偵錯資訊的物件。 您可能想要重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項。  
  
 如果某些程式庫中的物件參考到不存在的檔案，就可能發生 LNK4204。 這種情形時重新建置方案例如目的檔可能會刪除，因為編譯錯誤而無法重建。 在此情況下，編譯與 **/Z7**，或 **/Fd**，以更新物件來參考單一檔案每個程式庫 （不是預設的.pdb 檔名稱）。  如需詳細資訊，請參閱 [/Fd (程式資料庫檔名)](../../build/reference/fd-program-database-file-name.md)。  請確定每次更新原始檔控制系統中，會與該媒體櫃儲存.pdb。