---
title: "無法簽署檔案 &#39;&lt;檔案名稱&gt;&#39;： &lt;錯誤&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31028"
  - "vbc31028"
helpviewer_keywords: 
  - "BC31028"
ms.assetid: 2cb22e75-5ee2-4e07-afc0-680a0bd543d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法簽署檔案 &#39;&lt;檔案名稱&gt;&#39;： &lt;錯誤&gt;
嘗試簽署指定的檔案時發生錯誤。 發生這個錯誤的原因有下列幾種︰  
  
-   權限不足。  
  
-   遺漏 Authenticode 簽署所需的系統檔案。  
  
-   參考了不存在的憑證或私密金鑰檔案。  
  
-   檔案名稱或 URL 的拼字錯誤。  
  
 **錯誤 ID︰**BC31028  
  
### 更正這個錯誤  
  
1.  輸入正確的憑證和私密金鑰檔案名稱。  
  
2.  如果您使用 Authenticode 簽署，請檢查 Signcode.exe 和 Javasign.dll 檔案存在，而且未設定其唯讀屬性。  
  
3.  確定您具有檔案的 `Write` 權限。  
  
## 請參閱  
 [File Signing Tool \(Signcode.exe\)](http://msdn.microsoft.com/zh-tw/2d299154-34ea-41ba-ad12-17075bb7e1db)   
 [Deployment and Authenticode Signing](http://msdn.microsoft.com/zh-tw/ecc3f059-da2e-445b-9b87-5b2978e2f8b2)