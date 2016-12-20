---
title: "此安裝不支援此專案類型 | Microsoft Docs"
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
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 此安裝不支援此專案類型
這個錯誤會在嘗試開啟需要 Software Development Kit \(SDK\) 的專案類型，卻為安裝於 Visual Studio 時發生。  舉例來說，如果開啟未安裝 Visual Studio SDK 的 Visual Studio，且又試圖開啟該 SDK 的專案檔，例如 VSIX 專案，則會發生此錯誤。如需 Visual Studio SDK 的詳細資訊，請參閱 [Extending Visual Studio](http://go.microsoft.com/fwlink/?LinkID=64968)。  
  
## 解決方法  
 您必須確認嘗試開啟的專案類型已安裝正確的 SDK。  
  
#### 確認是否已安裝 SDK。  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的左窗格中，依序展開 \[**已安裝**\] 節點、\[**範本**\] 節點，然後選擇 \[**其他專案類型**\] 節點。  
  
3.  檢閱可用的專案類型，以確認嘗試開啟的專案是否可用。  
  
 如果找不到您嘗試開啟的專案類型，表示您沒有安裝關聯的 SDK。  您必須尋找並安裝關聯的 SDK 以開啟此專案類型。  
  
## 請參閱  
 [Visual Studio 2015 的新功能](../Topic/What's%20New%20in%20Visual%20Studio%202015.md)   
 [移植、移轉和升級 Visual Studio 專案](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md)