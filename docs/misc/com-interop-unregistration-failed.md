---
title: "COM Interop unregistration failed | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
嘗試將組件舊複本移除註冊時發生問題。  
  
 如果設定了 \[**註冊 COM Interop**\] 屬性，那麼專案系統將會在註冊剛建置的複本之前，先試圖移除註冊 COM 物件的舊複本。  這項作業的執行是為了將登錄保持為目前狀態。  
  
 請參閱 \[組態屬性\] 資料夾中的 \[**建置**\] 屬性頁，以存取 \[**註冊 COM Interop**\] 屬性。  
  
 一些可能的失敗原因包括：  
  
-   無法將組件先前的型別程式庫移除註冊。  這可能是登錄內的使用權限問題。  
  
-   無法將舊組件移除註冊。  這也可能是登錄內的使用權限問題。  
  
 如果移除註冊處理序失敗，可能會出現 CoCreatable 物件的 GUID 遺漏，以及任何型別程式庫 GUID 的遺漏。  但是整個建置處理序仍會成功。  
  
## 請參閱  
 [COM Interoperability in .NET Framework Applications](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)