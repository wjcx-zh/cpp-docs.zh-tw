---
title: "CLS 符合性警告 CLS01303 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01303"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01303"
ms.assetid: a8aa0cda-a2dd-41da-bcc2-53221207ea70
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01303
符合 CLS 標準的常值必須具有欄位初始化中繼資料所指定的值，這個中繼資料與常值完全相同 \(如果該常值是列舉，則為基礎類型\)。  
  
 常值靜態欄位的值是透過使用欄位初始化中繼資料來指定。 符合 CLS 標準的常值必須具有欄位初始化中繼資料所指定的值，這個中繼資料與常值完全相同 \(如果該常值是列舉，則為基礎類型\)。  
  
 請確定欄位常值的類型與常值完全相同 \(如果常值是列舉，則為基礎類型\)。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS01303：  
  
```  
.field public static literal char Field2 = int32(0x00000002)  
```  
  
 將初始設定式的類型設為與常值類型相同，即可解決這個警告：  
  
```  
.field public static literal char Field2 = char(0x00000002)  
```