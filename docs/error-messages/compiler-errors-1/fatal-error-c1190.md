---
title: "嚴重錯誤 C1190 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1190
dev_langs:
- C++
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e44afcd9cf35a2b1c438bc5ab91bebfe3260d53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1190"></a>嚴重錯誤 C1190
Managed 目標程式碼需要 '/clr' 選項  
  
 您使用 CLR 建構，但未指定 **/clr**。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下列範例會產生 C1190：  
  
```  
// C1190.cpp  
// compile with: /c  
__gc class A {};   // C1190  
ref class A {};  
```