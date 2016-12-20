---
title: "Visual Studio Library 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio Library, 概觀"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Visual Studio Library 概觀
Visual Studio 的程式庫是一組簡化的 VSPackages，原生 c \+ \+ 中建立樣板架構 c \+ \+ 類別。  Visual Studio 程式庫包含完整的原始程式碼，例如一疊 c \+ \+ 標頭檔。  標頭檔會安裝在 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration \\Common\\Source\\CPP\\VSL\\Include\\。  
  
> [!NOTE]
>  Visual Studio 程式庫會利用在作用中範本程式庫 \(ATL\) 的 COM 物件的支援。  如需詳細資訊，請參閱 [ATL 簡介](../atl/introduction-to-atl.md)。  
  
 Visual Studio 的媒體櫃支援單元測試，同時它自己的程式碼和程式碼。  部分的單元測試都包括在內，，如下所示：  
  
-   Visual Studio 文件庫的單元測試安裝在 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\UnitTest\\。  
  
-   您的程式碼的單元測試的基底類別是在 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\VSLUnitTest.h。  
  
 模擬 \(mock\) 實作的常用的 COM 和 Visual Studio 的介面是在標頭檔，VSLMockSystemInterfaces.h 和 VSLMockVisualStudioInterfaces.h，這安裝在 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\。  
  
## 請參閱  
 [使用 Visual Studio Library 開發 VSPackages](../misc/developing-vspackages-by-using-the-visual-studio-library.md)