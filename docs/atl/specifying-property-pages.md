---
title: "Specifying Property Pages | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ISpecifyPropertyPages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISpecifyPropertyPages method"
  - "屬性頁, 指定"
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Specifying Property Pages
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立 ActiveX 控制項，您通常會想要與可用於設定控制項的屬性的屬性頁。  容器控制項使用屬性頁來設定控制項的屬性的 **ISpecifyPropertyPages** 介面來探索。  您將需要實作在控制項中的這個介面。  
  
 使用 ATL，若要實作 **ISpecifyPropertyPages** ，請執行下列步驟:  
  
1.  從 [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)衍生您的類別。  
  
2.  將 **ISpecifyPropertyPages** 的項目加入至類別的 COM 對應。  
  
3.  將 [PROP\_PAGE](../Topic/PROP_PAGE.md) 項目加入至每個頁面的屬性對應與您的控制項。  
  
> [!NOTE]
>  當產生標準控制項使用 [ATL 控制項精靈](../atl/reference/atl-control-wizard.md)，您只需要加入到屬性的 `PROP_PAGE` 輸入對應。  精靈會產生其他步驟的必要的程式碼。  
  
 行為良好的容器中顯示指定的屬性頁按鈕與在屬性的 `PROP_PAGE` 輸入對應的順序。  一般而言，您應該在您的自訂頁面項目後面放置標準屬性頁面項目在屬性對應，因此，使用者先參閱頁面專屬的控制項。  
  
## 範例  
 月曆控制項的下列類別使用 **ISpecifyPropertyPages** 介面呼叫容器使用自訂日期網頁和股票色彩頁面，但可設定其屬性。  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/CPP/specifying-property-pages_1.h)]  
  
## 請參閱  
 [屬性頁](../atl/atl-com-property-pages.md)   
 [ATLPages 範例](../top/visual-cpp-samples.md)