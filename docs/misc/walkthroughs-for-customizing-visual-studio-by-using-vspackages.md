---
title: "逐步解說如何使用 VSPackage 自訂 Visual Studio | Microsoft Docs"
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
  - "VSPackage"
  - "教學課程"
  - "自訂 Visual Studio"
  - "VS IDE"
  - "Visual Studio IDE"
ms.assetid: 7d10e376-74de-4402-9c10-ee9c9aa33c98
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# 逐步解說如何使用 VSPackage 自訂 Visual Studio
您可以藉由建立 VSPackage 擴充 Visual Studio。 這些是 Visual Studio 本身的組成軟體模組。 工具視窗、編輯器、服務和專案類型全都是 VSPackage。 Visual Studio SDK 可讓您建立自己的 VSPackage。  
  
 本節的逐步解說教導如何建立 VSPackages、提供它們功能、將它們整合到 Visual Studio 中，然後將它們散發給其他使用者。 如需有關 VSPackage 和其功能的詳細資訊，請參閱 [在 Visual Studio SDK](../Topic/Inside%20the%20Visual%20Studio%20SDK.md)。  
  
## 在本節中  
 [建立擴充功能的功能表命令](../Topic/Creating%20an%20Extension%20with%20a%20Menu%20Command.md)  
 示範如何在 Visual Studio 中建立將命令加入功能表的 VSPackage，以及如何將鍵盤快速鍵加入命令。 同時也會示範如何將封裝的詳細資訊加入 Visual Studio 中的 \[關於\] 對話方塊和開頭顯示畫面。  
  
 [加入工具視窗](../Topic/Adding%20a%20Tool%20Window.md)  
 示範如何在 Visual Studio 中建立工具視窗，然後如何內嵌控制項，以及如何加入命令列。 同時也會顯示如何註冊工具視窗以便放置在 Visual Studio 中。  
  
 [擴充屬性、 工作清單、 輸出和選項\] 視窗](../Topic/Extending%20the%20Properties,%20Task%20List,%20Output,%20and%20Options%20Windows.md)  
 示範如何建置可讓使用者將工作加入 Visual Studio \[工作清單\] 和 \[輸出\] 視窗的基本工作管理員。 新增的工作可以在 Visual Studio \[屬性\] 視窗中編輯。 同時也會示範如何將頁面加入 \[選項\] 對話方塊。  
  
## 相關章節  
 [Visual Studio SDK 簡介](../Topic/Introducing%20the%20Visual%20Studio%20SDK.md)  
 提供隨附於 Visual Studio SDK 的功能和工具的概觀，以及如何使用它們來擴充 Visual Studio。  
  
 [在 Visual Studio SDK](../Topic/Inside%20the%20Visual%20Studio%20SDK.md)  
 描述如何自訂 Visual Studio IDE 的不同項目。