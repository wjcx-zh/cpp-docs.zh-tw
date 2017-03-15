---
title: "連結器工具警告 LNK4247 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4247"
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

進入點 \(Entry Point\) 'decorated\_function\_name' 已經有執行緒屬性；已忽略 'attribute'  
  
 進入點是以 [\/ENTRY \(進入點符號\)](../../build/reference/entry-entry-point-symbol.md) 指定，具有執行緒屬性，但是又用不同的執行緒模型指定了 [\/CLRTHREADATTRIBUTE \(設定 CLR 執行緒屬性\)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)。  
  
 連結器已忽略以 \/CLRTHREADATTRIBUTE 指定的值。  
  
 若要解除這項警告：  
  
-   從組建中移除 \/CLRTHREADATTRIBUTE。  
  
-   從原始程式碼檔案移除屬性。  
  
-   從原始程式碼檔移除屬性，並從組建移除 \/CLRTHREADATTRIBUTE，然後接受預設 CLR 執行緒模型。  
  
-   變更傳遞給 \/CLRTHREADATTRIBUTE 的值，讓它與原始程式碼檔中的屬性一致。  
  
-   變更原始程式碼檔中的屬性，讓它與傳遞給 \/CLRTHREADATTRIBUTE 的值一致。  
  
 下列範例會產生 LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```