---
title: "如何：將範本新增至新增專案對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "對話方塊, 將範本新增至專案"
  - "專案 [Visual Studio SDK], 將範本新增至對話方塊"
  - "範本 [Visual Studio], 新增至專案對話方塊"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 如何：將範本新增至新增專案對話方塊
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安裝期間會安裝一些預先定義的專案範本。 如需預先定義之專案範本的完整清單，請參閱 [NIB 根據範本建立專案](http://msdn.microsoft.com/zh-tw/7c36d86a-6b79-4480-8228-0f925f1204b2)。 除了預設專案範本之外，您還可以建立自訂或特定子類型的專案範本。 例如，**智慧型裝置**子類型針對 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 專案提供自己的範本。 如需如何建立自訂範本的相關指示，請參閱[如何：建立專案範本](../Topic/How%20to:%20Create%20Project%20Templates.md)。  
  
## 將範本新增至新增專案對話方塊  
  
#### 將範本新增至新增專案對話方塊  
  
1.  建立包含 MyTemplate.vstemplate 檔案的範本。  
  
2.  在包含 .vstemplate 檔的範本中選取檔案並按一下滑鼠右鍵，然後按一下 \[傳送到\]，再按一下 \[壓縮的 \(zipped\) 資料夾\]。 您先前擷取的檔案會壓縮成 .zip 檔。  
  
 將 .zip 範本檔放在 **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates** 中。  
  
## 請參閱  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [NIB：Visual Studio 範本](http://msdn.microsoft.com/zh-tw/141fccaa-d68f-4155-822b-27f35dd94041)   
 [導致加入新項目對話方塊](../Topic/Contributing%20to%20the%20Add%20New%20Item%20Dialog%20Box.md)