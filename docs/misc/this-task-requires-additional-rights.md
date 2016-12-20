---
title: "這項工作需要額外的權限 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UACDialog"
ms.assetid: a03d3509-5e6e-411a-9aec-0766d7ee3a0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 這項工作需要額外的權限
這個錯誤時，如果 Visual Studio 命令的帳戶沒有足夠的使用權限完成作業的使用者叫用。  
  
 必須執行一些 Visual Studio 命令與使用者具有足夠的存取權限讓命令讀取或寫入所有必要檔案和登錄機碼的帳戶。  若要取得這些權限，您必須先關閉然後再以具更高存取權限的帳戶執行 Visual Studio，例如系統管理員。  
  
 如需使用權限的詳細資訊在執行 Visual Studio，請參閱 [使用者權限](../Topic/User%20Permissions%20and%20Visual%20Studio.md)。  
  
### 若要更正這個錯誤  
  
1.  在對話方塊中，按一下 \[**使用其他帳戶重新啟動**\]。  
  
     這會提示您將目前載入的方案，然後關閉 Visual Studio 並重新啟動，提示您切換至不同的帳戶。  
  
2.  在提示您登入時，請使用比先前帳戶具有更高權限的帳戶登入，例如 Administrator。  
  
     在 Visual Studio 啟動時，它會重新載入上次方案和命令列。  
  
> [!NOTE]
>  登入具有更高權限的帳戶不一定保證 Visual Studio 命令運作。  有些命令可能未能成功執行，即使您使用系統管理員帳戶。