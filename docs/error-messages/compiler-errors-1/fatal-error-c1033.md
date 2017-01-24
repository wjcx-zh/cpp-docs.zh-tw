---
title: "嚴重錯誤 C1033 | Microsoft Docs"
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
  - "C1033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1033"
ms.assetid: 09976c03-8450-4cf7-8b43-1b91c2c2b9f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟程式資料庫 pdb  
  
 這項錯誤可能是因磁碟錯誤而造成。  
  
 在 Visual C\+\+ .NET 2002 中，當檔案名稱 \(或該檔案名稱的目錄路徑\) 包含 MBCS 字元時，使用者地區設定 \(Locale\) 一定要正確設定。  設定系統地區設定仍然不夠；使用者地區必須設定才能處理 MBCS 字元。  
  
 如需詳細資訊，請參閱 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;246007](http://support.microsoft.com/default.aspx?scid=kb;en-us;246007)。