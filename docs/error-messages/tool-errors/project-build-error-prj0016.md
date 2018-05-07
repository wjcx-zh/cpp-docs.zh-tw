---
title: 專案建置錯誤 PRJ0016 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6184e5bb251a2b74e8500cc195a38f2d814c1b5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0016"></a>專案建置錯誤 PRJ0016
使用者的安全性設定會防止建立處理程序。 這些設定所需的建置。  
  
 您沒有建立處理程序的程序的權限使用者的身分登入。 您必須變更此使用者帳戶的權限等級，或連絡您的帳戶管理員。  
  
 如果已設定下列登錄機碼，也會發生這個錯誤：  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 若要解決這個錯誤，刪除 RestrictRun 索引鍵。 如需此登錄機碼，附加**vcspawn.exe**的索引鍵中的項目清單。  
  
 此錯誤的另一個原因是，您的原則設定不包含 VCSpawn.exe 登錄機碼 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun 下做為此使用者帳戶允許的視窗程式。  
  
 如需詳細資訊，請參閱：  
  
-   知識庫文章 324153，可用於[ http://support.microsoft.com/default.aspx?scid=kb; en-us-我們; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153)。  
  
-   [系統原則設定遵守](http://msdn.microsoft.com/library/aa372139)的 「 執行只允許 Windows 應用程式 」 一節。