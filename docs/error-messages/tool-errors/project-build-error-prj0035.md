---
title: "專案建置錯誤 PRJ0035 | Microsoft Docs"
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
  - "PRJ0035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0035"
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 檔案 'file' 包含無法轉譯成使用者 ANSI 字碼頁的 Unicode 內容。  
  
 ***UNICODE 檔案內容***  
  
 ***file***  為 XML 檔案，建立為 Web 部署工具的命令列。  
  
 專案系統發現 Web 部署屬性頁的某種屬性之 Unicode 字元，無法正確地轉譯為 ANSI。  
  
 這個錯誤的解決方法是，更新使用 ANSI 的屬性內容，或在您電腦上安裝該字碼頁，並將它設為系統預設值。