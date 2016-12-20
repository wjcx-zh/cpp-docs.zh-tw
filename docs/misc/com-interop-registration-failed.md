---
title: "COM Interop registration failed | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop registration failed
向 COM 用戶端公開功能的組件註冊失敗。  如果發生這種錯誤，建置處理序將無法完成。  
  
 組件可以向 COM 用戶端公開物件。  專案系統提供屬性 \(Property\) 以註冊 COM Interop 的公開類別，並產生和註冊型別程式庫，使這些類別可從指令碼語言或 Visual Basic 6 來使用。  
  
 請參閱 \[**組態屬性**\] 資料夾中的 \[**建置**\] 屬性頁，以存取 \[**註冊 COM Interop**\] 屬性。  
  
 一些可能的失敗原因包括：  
  
-   無法產生組件的型別程式庫。  這可能是磁碟空間問題或是由 Visual Studio 或某些其他處理序鎖定的型別程式庫的檔案鎖定問題。  並且參考組件的型別程式庫無法正確地在您系統上註冊。  
  
-   無法註冊已產生的型別程式庫。  這可能是登錄內的使用權限問題。  
  
-   無法在組件內註冊類別。  這可能是登錄內的使用權限問題。  
  
 **若要更正這個錯誤**  
  
-   在您電腦上建立一些可用磁碟空間。  
  
-   如果發生檔案鎖定的問題，請重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
-   請確定您是以系統管理員的身分或是以具有存取登錄權限之群組成員的身分進行登入。  
  
## 請參閱  
 [COM Interoperability in .NET Framework Applications](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)