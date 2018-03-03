---
title: "連結器工具錯誤 LNK2008 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7c2fecff55677653c25c7d87fb22fa984526159
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2008"></a>連結器工具錯誤 LNK2008
修復目標不是對齊 'symbol_name'  
  
 您未正確對齊的目的檔中找到修復目標連結。  
  
 這個錯誤可能因自訂 secton 對齊方式 (例如 #pragma[套件](../../preprocessor/pack.md))，[對齊](../../cpp/align-cpp.md)修飾詞，或使用組件語言程式碼會修改 secton 對齊方式。  
  
 如果您的程式碼不使用任何上述，原因可能是由編譯器。