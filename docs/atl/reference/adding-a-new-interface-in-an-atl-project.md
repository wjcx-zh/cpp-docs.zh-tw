---
title: "將新介面加入至 ATL 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.interface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 增加介面"
  - "控制項 [ATL], 介面"
  - "實作介面 ATL 精靈"
  - "介面, 加入至 ATL 物件"
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 將新介面加入至 ATL 專案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您將介面加入至物件或控制項時，您會為介面的每個方法建立截短的函式。  在物件或控制項中，您只能加入目前在現有型別程式庫中找到的介面。  此外，您加入介面的類別必須實作 [BEGIN\_COM\_MAP](../Topic/BEGIN_COM_MAP.md) 巨集，或是如果專案是屬性化的，它必須具有 `coclass` 屬性。  
  
 您可利用兩種方式來將新介面加入至控制項：手動或使用 \[類別檢視\] 中的程式碼精靈。  
  
### 若要使用類別檢視中的程式碼精靈來將介面加入至現有物件或控制項  
  
1.  在[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中以滑鼠右鍵按一下控制項的類別名稱。  例如，完整控制項或複合控制項 \(Composite Control\)，或是在標頭檔中實作 BEGIN\_COM\_MAP 巨集的任何其他控制項類別。  
  
2.  在捷徑功能表中按一下 \[加入\]，再按 \[**實作介面**\]。  
  
3.  在[實作介面精靈](../../ide/implement-interface-wizard.md)中選取要實作的介面。  如果介面不存在於任何可用的型別程式庫當中，則您必須手動將它加入至 .idl 檔。  
  
### 若要手動加入新介面  
  
1.  將新介面的定義加入至 .idl 檔。  
  
2.  從介面衍生物件或控制項。  
  
3.  為介面建立新的 [COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20\(ATL\).md)，或是如果專案是屬性化的，則加入 `coclass` 屬性。  
  
4.  在介面上實作方法。  
  
## 請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)