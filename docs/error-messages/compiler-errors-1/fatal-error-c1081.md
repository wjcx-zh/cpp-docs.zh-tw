---
title: "嚴重錯誤 C1081 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bac4aaf0d4aebcbc34f74b6ccb91170fd4224e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1081"></a>嚴重錯誤 C1081
'symbol': 檔名太長  
  
 檔案路徑名稱的長度超過`_MAX_PATH`（定義由 STDLIB.h 為 260 個字元）。 請縮短檔案的名稱。  
  
 如果您具有短的檔名呼叫 CL.exe，可能需要編譯器產生完整的路徑名稱。 例如，`cl -c myfile.cpp`可能會導致編譯器產生：  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```