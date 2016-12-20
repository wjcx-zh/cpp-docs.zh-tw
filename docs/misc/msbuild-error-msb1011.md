---
title: "MSBuild 錯誤 MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1011
**請指定要使用哪個專案檔或方案檔，因為這個資料夾包含一個以上的專案檔或方案檔。**  
  
 如果命令列上未指定專案檔，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 就會在目前的工作目錄中尋找副檔名為 "proj" 或 "sln" 的檔案來使用。  但是目前工作目錄中有一個以上副檔名為 "proj" 或 "sln" 的檔案。  
  
### 若要更正這個錯誤  
  
1.  在命令列上加入專案檔名。  例如，不使用 `msbuild`，而改為輸入 `msbuild myapp.proj`。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)