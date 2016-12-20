---
title: "COM Interop Wrapper Error | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyassembly"
  - "Vs.refruntlbimp"
helpviewer_keywords: 
  - "COM Interop Wrapper dialog box"
ms.assetid: 9a9d6374-ee26-4dbc-9e34-e1d90f6254b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop Wrapper Error
當專案系統無法為特定元件建立 COM interop 包裝函式時，就會顯示此訊息方塊。  Common Language Runtime \(CLR\) 需要 COM interop 包裝函式才能管理 COM 元件並與之通訊。  如需詳細資訊，請參閱 [Visual Basic 和 C\# 中的 COM 互通性](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)。  
  
 失敗的常見原因包括：  
  
-   未正確註冊元件的類型程式庫。  
  
-   您的電腦上找不到被包裝的元件所相依的元件。  
  
 在這兩種情況下，您需要確定 COM 元件已正確安裝並註冊在您的電腦上，然後重試作業。  
  
> [!TIP]
>  您也可以在 [MSDN 網站](http://go.microsoft.com/fwlink/?LinkId=3355)搜尋特定 COM 元件已發行的 COM interop 包裝函式。  
  
> [!NOTE]
>  COM interop 包裝函式有時稱為「主要 interop 組件」。 這些詞彙是同義字  
  
## 請參閱  
 [Visual Studio 中的元件模型命名空間](http://msdn.microsoft.com/zh-tw/705d0add-0707-44ba-a6de-637381d9c937)   
 [元件撰寫](../Topic/Component%20Authoring.md)   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)   
 [COM Interoperability in .NET Framework Applications](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)