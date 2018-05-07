---
title: 連結器工具警告 LNK4247 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6096bbfba9c60d8ed28aa660d078cd155f0316a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4247"></a>連結器工具警告 LNK4247
進入點 'decorated_function_name' 已經有執行緒屬性;忽略 ' attribute'  
  
 進入點，以指定[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)，有執行緒屬性，但[/CLRTHREADATTRIBUTE （設定 CLR 執行緒屬性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)也指定了，具有不同的執行緒模型。  
  
 連結器會忽略 /CLRTHREADATTRIBUTE 與指定的值。  
  
 若要解決這個警告：  
  
-   /CLRTHREADATTRIBUTE 移除您的組建。  
  
-   從您的原始程式碼檔中移除屬性。  
  
-   從來源和 /CLRTHREADATTRIBUTE 移除這兩個屬性，從您的組建，並接受預設的 CLR 執行緒模型。  
  
-   變更傳遞至 /CLRTHREADATTRIBUTE 的值，使它同意來源中的屬性。  
  
-   變更來源中的屬性，使其以值傳遞至 /CLRTHREADATTRIBUTE 同意。  
  
 下列範例會產生 LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```