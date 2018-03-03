---
title: "資源編譯器警告 RC4005 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f27de973f0ff18493c182bdf1feb3f2812f39af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4005"></a>資源編譯器警告 RC4005
'identifier': 巨集重新定義  
  
 識別項定義了兩次。 編譯器會使用第二個巨集定義。  
  
 這個警告可能因命令列上的程式碼中定義巨集`#define`指示詞。 它也可能被因從 include 檔匯入的巨集。  
  
 若要排除警告，請移除其中一個定義，或使用`#undef`指示詞之前的第二個定義。