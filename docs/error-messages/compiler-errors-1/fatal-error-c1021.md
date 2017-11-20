---
title: "嚴重錯誤 C1021 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1021
dev_langs: C++
helpviewer_keywords: C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aa56ca51293bd5afd6baeeabe11b21159ce8b98e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1021"></a>嚴重錯誤 C1021
無效的前置處理器命令 'string'  
  
 `string` 不是有效的 [前置處理器指示詞](../../preprocessor/preprocessor-directives.md)。 若要解決這個錯誤，請使用 `string`的有效前置處理器名稱。  
  
 下列範例會產生 C1021：  
  
```  
// C1021.cpp  
#BadPreProcName    // C1021 delete line  
```