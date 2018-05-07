---
title: 連結器工具警告 LNK4070 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e4599e96552f1b98ef0b1af8d38995ebbe5a83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4070"></a>連結器工具警告 LNK4070
/OUT:filename 指示詞中。EXP 與輸出檔名 'filename';忽略指示詞  
  
 `filename`中所指定[名稱](../../build/reference/name-c-cpp.md)或[文件庫](../../build/reference/library.md)陳述式建立.exp 檔時不同的輸出`filename`，已假設為預設值，或指定[/Out](../../build/reference/out-output-file-name.md)選項。  
  
 如果您變更在開發環境中和未更新專案的.def 檔的輸出檔名稱，您會看到這個警告。 手動更新.def 檔案，若要解決這個警告。  
  
 使用產生的 DLL 的用戶端程式可能會遇到的問題。