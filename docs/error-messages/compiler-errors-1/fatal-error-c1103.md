---
title: "嚴重錯誤 C1103 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1103
dev_langs:
- C++
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f35bcec3b89e8e6c95740d1efb2dbbe98851f1a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1103"></a>嚴重錯誤 C1103
匯入 progid 時發生嚴重錯誤: 'message'  
  
 編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 progid 來指定類型程式庫，同時又指定 `no_registry`。  
  
 如需詳細資訊，請參閱[#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下列範例會產生 C1103：  
  
```  
// C1103.cpp  
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```