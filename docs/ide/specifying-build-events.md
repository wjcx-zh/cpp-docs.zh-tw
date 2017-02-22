---
title: "指定建置事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.IVCEventTool.CommandLine"
  - "VC.Project.IVCEventTool.ExcludedFromBuild"
  - "VC.Project.IVCEventTool.Description"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建置事件 [C++]"
  - "建置事件 [C++], 指定"
  - "組建 [C++], 自訂 C++"
  - "組建 [C++], 事件"
  - "自訂建置步驟 [C++], 建置事件"
  - "事件 [C++], 組建"
  - "建置後事件"
  - "連結前事件"
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 指定建置事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用建置事件來指定要在建置開始前、連結程序開始前或建置完成後執行的命令。  
  
 只有在該建置成功地抵達建置程序中的這些點時，才會執行建置事件。  如果在建置中發生了錯誤，「*建置後*」\(Post\-Build\) 事件就不會發生；如果錯誤是發生在連結階段之前，則「*連結前*」\(Pre\-Link\) 或「*建置後*」\(Post\-Build\) 事件都不會發生。  此外，如果沒有檔案需要連結，那麼「*連結前*」\(Pre\-Link\) 事件就不會發生。  在不含連結步驟的專案中也不會有「*連結前*」\(Pre\-Link\) 事件。  
  
 如果沒有檔案需要建置，那麼建置事件也不會發生。  
  
 如需建置事件的一般資訊，請參閱[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)。  
  
### 若要指定建置事件  
  
1.  在 \[**方案總管**\] 中，選取您要指定建置事件的專案。  
  
2.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
3.  在 \[**建置事件**\] 資料夾中，選取建置事件屬性頁。  
  
4.  指定與建置事件關聯的屬性：  
  
    -   在 \[**命令列**\] 中指定命令，如同在命令提示字元中指定命令一般。  指定有效的命令或批次檔以及所有需要的輸入檔或輸出檔。  在批次檔名稱前面指定 **call** 批次命令，以確保所有的後續命令都會被執行。  
  
         多個輸入檔和輸出檔可利用 MSBuild 巨集以符號形式加以指定。  [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]以進一步了解如何指定檔案位置或檔案集合名稱，請參閱[建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)。  
  
         由於 MSBuild 會保留 '%' 字元，因此如果您指定環境變數，請將 **%** 逸出字元取代為 **%25** 十六進位逸出序列。  例如，將 **%WINDIR%** 取代為 **%25WINDIR%25**。  MSBuild 會在存取環境變數之前，將每個 **%25** 序列取代為 **%** 字元。  
  
    -   在 \[**描述**\] 中，輸入此事件的描述。  當此事件發生時，該描述將會顯示在 \[**輸出**\] 視窗中。  
  
    -   在 \[**從組建排除**\] 中，如果您不希望該事件執行，請指定 \[**是**\]。  
  
## 請參閱  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)   
 [建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)   
 [疑難排解組建自訂](../ide/troubleshooting-build-customizations.md)