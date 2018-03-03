---
title: "連結器工具警告 LNK4070 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c3c683593b9019851b1a330a613adcf7a18c4a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4070"></a>連結器工具警告 LNK4070
/OUT:filename 指示詞中。EXP 與輸出檔名 'filename';忽略指示詞  
  
 `filename`中所指定[名稱](../../build/reference/name-c-cpp.md)或[文件庫](../../build/reference/library.md)陳述式建立.exp 檔時不同的輸出`filename`，已假設為預設值，或指定[/Out](../../build/reference/out-output-file-name.md)選項。  
  
 如果您變更在開發環境中和未更新專案的.def 檔的輸出檔名稱，您會看到這個警告。 手動更新.def 檔案，若要解決這個警告。  
  
 使用產生的 DLL 的用戶端程式可能會遇到的問題。