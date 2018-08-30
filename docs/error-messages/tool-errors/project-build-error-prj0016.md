---
title: 專案建置錯誤 PRJ0016 |Microsoft Docs
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
ms.openlocfilehash: 8c07de9e766b7c2126d0ce4c8d1daed631a8355c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194736"
---
# <a name="project-build-error-prj0016"></a>專案建置錯誤 PRJ0016
使用者的安全性設定會防止建立處理程序。 這些設定所需的建置項目。  
  
 您會建立使用程序的程序的權限的使用者身分登入。 您必須變更此使用者帳戶的權限等級，或連絡您的帳戶管理員。  
  
 如果設定下列登錄機碼，也會發生此錯誤：  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 若要解決這個錯誤，刪除 RestrictRun 索引鍵。 如果需要此登錄機碼，附加**vcspawn.exe**的機碼中的項目清單。  
  
 此錯誤的另一個原因是，您的原則設定不包含 VCSpawn.exe 登錄機碼 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun 下做為此使用者帳戶允許的視窗程式。  
  
 如需詳細資訊，請參閱：  
  
-   眭妎踱恅 324153，其位於[ http://support.microsoft.com/default.aspx?scid=kb; en-us-我們; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153)。  
  
-   [遵守系統原則設定](https://msdn.microsoft.com/library/aa372139)，「 執行只允許 Windows 應用程式 」 一節。