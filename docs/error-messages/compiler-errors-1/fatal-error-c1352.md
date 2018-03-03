---
title: "嚴重錯誤 C1352 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f2a5c42eaa5afc609f1b8ee1c09875db8bff9c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1352"></a>嚴重錯誤 C1352
函式 'function' (位於模組 'file' 中) 的 MSIL 無效或損毀  
  
 .netmodule 已傳遞至編譯器，但編譯器偵測到檔案損毀。  請要求產生 .netmodule 的人員調查。  
  
 編譯器不會檢查所有類型之損毀的 .netmodule 檔案。  但會確認函式中的所有控制路徑都包含 return 陳述式。  
  
 如需詳細資訊，請參閱 [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。