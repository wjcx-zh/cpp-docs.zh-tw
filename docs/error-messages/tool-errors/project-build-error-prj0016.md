---
title: "專案建置錯誤 PRJ0016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0016"
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 專案建置錯誤 PRJ0016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用者的安全性設定防止建立處理序，建置時需要這些設定。  
  
 您登入的使用者身分沒有使用一個處理序建立更多處理序的權限。  您必須變更此使用者帳戶的權限等級，或是連絡您的帳戶管理員。  
  
 如果設定了下列登錄機碼 \(Registry Key\)，則也可能發生這個錯誤：  
  
 \\\\HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Policies\\Explorer\\RestrictRun  
  
 若要解決這個錯誤，請刪除 RestrictRun 機碼。  如果需要這個登錄機碼，請將 **vcspawn.exe** 附加至機碼中的項目清單。  
  
 導致這個錯誤的另一項原因是，您的原則設定 \(Policy Setting\) 不包括在登錄機碼 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\Policies\\RestrictRun 下的 VCSpawn.exe 檔，該檔是容許給此使用者帳戶執行的視窗程式。  
  
 如需詳細資訊，請參閱：  
  
-   知識庫文件 324153，其可用於 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153)。  
  
-   [遵循系統原則設定](http://msdn.microsoft.com/library/aa372139)，此章節討論「只執行允許執行的 Windows 應用程式」。