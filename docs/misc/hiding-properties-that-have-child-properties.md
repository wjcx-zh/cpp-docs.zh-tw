---
title: "隱藏具有子屬性的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性 [Visual Studio SDK], 隱藏"
  - "屬性視窗, 隱藏具有子屬性的屬性"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 隱藏具有子屬性的屬性
您會想要隱藏具有子屬性的屬性：  
  
-   如果您有巢狀的專案的父專案以程式設計方式控制子專案的某些方面。  
  
-   如果您使用特殊的設計工具中使用控制項，並不想讓開發人員之控制項的所有內容的完整存取權。  
  
-   如果您有範圍的物件的擁有權，但想限制屬性的檢視。  
  
### 若要隱藏具有子屬性的屬性  
  
1.  Set the `pfDisplay` parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> to `FALSE`.  
  
2.  Set the `pfHide` parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> to `TRUE`.  
  
## 請參閱  
 [屬性顯示格線](../Topic/Properties%20Display%20Grid.md)