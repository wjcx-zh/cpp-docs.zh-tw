---
title: "加入屬性 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "介面, 加入屬性"
  - "屬性 [C++], 加入至介面"
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入屬性 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用[加入屬性精靈](../ide/names-add-property-wizard.md)將方法加入專案中的介面。  
  
### 若要將屬性加入至物件  
  
1.  在[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，對要加入屬性的介面名稱按一下滑鼠右鍵。  
  
    > [!NOTE]
    >  您也可以將屬性加入至分配介面 \(Disinterface\)，除非專案已經屬性化，否則分配介面位於程式庫節點之內。  
  
2.  從捷徑功能表中，按一下 \[加入\]，再按一下 \[**加入屬性**\]。  
  
3.  在[加入屬性精靈](../ide/names-add-property-wizard.md)中提供建立屬性的資訊。  
  
4.  在精靈中的 [IDL 屬性](../ide/idl-attributes-add-property-wizard.md)頁面上，對此屬性指定任一個介面定義語言 \(IDL\) 設定。  
  
5.  按一下 \[完成\] 以加入屬性。  
  
 屬性的 **Get** 和 `Put` 方法在類別檢視中，屬性定義的介面下方，以兩個圖示表示。  您可以按兩下任一個圖示來檢視 .idl 檔內的屬性宣告。  
  
-   ATL 介面的 **Get** 和 **Put** 函式加入至 .cpp 檔，並且此函式的參考加入至 .h 檔。  
  
-   如果您為 MFC 分配介面選擇 \[成員變數\] 做為實作 \(Implementation\) 類型，則會加入一個方法和變數至實作它的類別上。  如果您選擇 \[Get\/Set 方法\] 做為實作類型，則會加入兩個方法至實作它的類別上。  
  
## 請參閱  
 [建立 COM 介面](../ide/creating-a-com-interface-visual-cpp.md)   
 [編輯 COM 介面](../ide/editing-a-com-interface.md)   
 [元件物件模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [介面指標和介面](http://msdn.microsoft.com/library/windows/desktop/ms688484)