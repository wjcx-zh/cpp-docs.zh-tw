---
title: "命令列警告 D9042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 命令列警告 D9042
無效的值 'value' \(對 '\/option' 而言\)，假設為 'value'。程式碼分析警告在這個版本的編譯器中無法使用  
  
 程式碼分析警告數字已加入 **\/wd**、**\/we**、**\/wo** 或 **\/wl** 命令列選項，且 **\/analyze** 已指定於不支援程式碼分析的平台上。 若要補救這個警告，請切換到 Visual Studio Team System 的 x86 版本，或移除 **\/analyze** 命令列選項。  
  
## 範例  
 下列命令列範例會在 x64 或 Itanium 系統上產生警告 D9042：  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 若要補救這個警告，請切換到 Visual Studio Team System 的 x86 版本，或移除 **\/analyze** 和 **\/wd6001** 命令列選項。  
  
## 請參閱  
 [命令列錯誤 D8000 至 D9999](../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [編譯器選項](../build/reference/compiler-options.md)