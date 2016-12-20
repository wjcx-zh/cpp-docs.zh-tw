---
title: ".SAFESEH | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".SAFESEH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registering functions as exception handlers"
  - "SAFESEH directive"
  - ".SAFESEH directive"
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAFESEH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

結構化的例外處理常式註冊函式。  
  
## 語法  
  
```  
  
.SAFESEH identifier  
```  
  
## 備註  
 *識別項* 必須是本機定義的識別碼 [程序](../../assembler/masm/proc.md) 或  [EXTRN](../../assembler/masm/extrn.md) 處理序  A [標籤](../../assembler/masm/label-masm.md)不允許。  。SAFESEH 指示詞需要 [\/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe 命令列選項。  
  
 如需有關結構化的例外處理常式的詳細資訊，請參閱 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。  
  
 比方說，如果要登錄的安全例外處理常式，建立新的 MASM 檔案 \(如下\)、 \/safeseh，與組合，和將它加入至連結的物件。  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)