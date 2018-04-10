---
title: 連結器工具警告 LNK4247 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 517605993199942f863faa78e14a022529214a64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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