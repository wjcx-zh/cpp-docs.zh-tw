---
title: "實作策略 | Microsoft Docs"
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
  - "VSPackage, 實作策略"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 實作策略
您可以使用自動化增益集、VSPackage、Managed Extensibility Framework \(MEF\) 或前三者的組合來擴充 Visual Studio。 一般而言，相較於 VSPackage 或 MEF 元件部分，增益集的開發工作比較容易，但功能較不強大。 增益集可以呼叫擴充性介面，而 VSPackage 和 MEF 元件部分可以存取 Visual Studio 自動化模型。 您可以結合數種不同的方法來建立有效的方案。  
  
 VSPackage 可在 Unmanaged 或 Managed 程式碼中撰寫。 建議您使用 Managed Package Framework \(MPF\)，在 Managed 程式碼中撰寫新的 VSPackage。 幾乎所有可在 Unmanaged 程式碼中撰寫的項目，都能在 Managed 程式碼中更輕鬆安全地實作。 不過，在 Unmanaged 程式碼中撰寫的舊版應用程式將會在 Visual Studio 中繼續執行。  
  
 您可以將簡單的擴充功能加入工具視窗中，或將資訊傳送至 Visual Studio UI 項目，例如狀態列或輸出視窗。 更複雜的應用程式可以撰寫成 Visual Studio 階層架構，例如伺服器總管。 但實作專案、編輯器或設計工具仍可取得更強大的功能。 例如，[!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 本身會以語言服務形式實作。  
  
## 相關章節  
 [Visual Studio SDK 和自動化](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 討論如何使用自動化、VSPackage 或其組合來建立 Visual Studio 擴充性應用程式。  
  
 [Visual Studio SDK 和 Managed 程式碼](../misc/visual-studio-sdk-and-managed-code.md)  
 比較不同的方式，在 Managed 程式碼中撰寫 VSPackage。  
  
 [Visual Studio IDE 概念](../misc/visual-studio-ide-concepts.md)  
 討論 VSPackage 及如何使用服務的基本概念。  
  
 [擴充 Visual Studio 的其他部分](../Topic/Extending%20Other%20Parts%20of%20Visual%20Studio.md)  
 討論 Visual Studio 中的一般 UI 應用程式項目，例如 \[狀態\] 和 \[輸出\] 視窗。  
  
 [在 Visual Studio 中的階層](../Topic/Hierarchies%20in%20Visual%20Studio.md)  
 提供 Visual Studio 階層架構的概觀，此階層架構會在整合式開發環境 \(IDE\) 中顯示為節點樹狀結構。  
  
 [專案](../Topic/Projects.md)  
 提供產品和方案類別的概觀。  
  
 [編輯器和語言服務擴充功能](../Topic/Editor%20and%20Language%20Service%20Extensions.md)  
 示範如何擴充程式碼和文字編輯器，以及如何建立自訂編輯器和設計工具。  
  
 [舊版的語言服務擴充性](../Topic/Legacy%20Language%20Service%20Extensibility.md)  
 示範如何建立語言服務。  
  
 [Visual Studio SDK 參考](../Topic/Visual%20Studio%20SDK%20Reference.md)  
 VSSDK 的參考文件。  
  
## 請參閱  
 [開始開發 Visual Studio 擴充功能](../Topic/Starting%20to%20Develop%20Visual%20Studio%20Extensions.md)