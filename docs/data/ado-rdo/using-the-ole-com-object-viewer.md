---
title: "使用 OLE/COM 物件檢視器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 檢視內部介面"
  - "Automation 物件的物件檢視器"
  - "OLE/COM 物件檢視器"
ms.assetid: a3359e31-2869-451d-9571-129b4e8b41f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 使用 OLE/COM 物件檢視器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 OLE\/COM 物件檢視器檢視控制項的介面。  
  
### 若要使用 OLE\/COM 物件檢視器  
  
1.  啟動 OLE\/COM 物件檢視器 \(oleview.exe\)，位於\\ Program Files \(x86\) \\ Windows Kits \\ 8.0 \\ bin \\ x86 \\ 資料夾。  
  
2.  於檢視器的 **原件類別** 目錄中，開啟 **自動物件** 資料夾以顯示所有登錄過的 Automation 物件。  
  
3.  選取控制項的其中一個。  某些索引標籤會出現在右邊窗格內 ; 由該控制項所實作的介面則顯示於 \[**Registry**\] 索引標籤。  
  
    -   如果您開啟左窗格的控制項的捷徑選單，並選取 \[**View Type Information**\]，ITypeInfo 檢視器就會顯示重建的 .idl 或 .odl 檔。  
  
    -   如果您展開左窗格內的控制項節點，會顯示此物件的介面清單。  如果您選取了介面，它的登錄項目會顯示在右窗格中。  
  
    -   如果您開啟介面的捷徑選單，並選取 \[**View**\]，OLE\/COM 物件檢視器會顯示對話方塊，裡面包含介面的 GUID，以及可檢視型別程式庫資訊 \(如果有的話\) 的選項。  選取 \[**View Type Information**\] 會將該介面特定的重建 .idl 檔的一部分顯示於 ITypeInfo 檢視器內。  
  
    -   在 ITypeInfo 檢視器，您可以在樹狀檢視選取介面成員，即可在右邊窗格內顯示存取子 \(Accessor\) 的方法簽章。  
  
## 請參閱  
 [使用 ActiveX 控制項](../../data/ado-rdo/using-activex-controls.md)