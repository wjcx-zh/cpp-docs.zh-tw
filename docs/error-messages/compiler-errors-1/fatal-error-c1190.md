---
title: 嚴重錯誤 C1190 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1190
dev_langs:
- C++
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 831eb782b074ed8ba0eb36d1abef7857321f2483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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