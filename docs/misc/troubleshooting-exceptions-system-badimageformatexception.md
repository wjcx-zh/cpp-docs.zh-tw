---
title: "疑難排解例外狀況：System.BadImageFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "BadImageFormatException 類別"
ms.assetid: 8d2b385a-3d6d-4dfa-8546-7ece562867e3
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.BadImageFormatException
當 DLL 或可執行程式的檔案映像無效時，就會擲回 <xref:System.BadImageFormatException> 例外狀況。  
  
## 相關秘訣  
 **如果您的應用程式使用 32 位元元件，請確定應用程式永遠會以 32 位元應用程式的形式執行。**  
 如果應用程式專案的 \[**平台目標**\] 屬性設定為 `AnyCPU`，則編譯的應用程式在 64 位元或 32 位元模式下都可以執行。 以 64 位元應用程式的形式執行時，Just\-In\-Time \(JIT\) 編譯器會產生 64 位元機器碼。 如果應用程式依賴 32 位元 Managed 或 Unmanaged 元件，則在 64 位元模式下會無法載入該元件。 若要解決這個問題，請將專案的 \[**平台目標**\] 屬性設定為 `x86`，然後重新編譯。  
  
 **請確定您沒有使用以不同 .NET Framework 版本建立的元件。**  
 當使用 [!INCLUDE[net_v10_short](../Token/net_v10_short_md.md)] 或 [!INCLUDE[net_v11_short](../misc/includes/net_v11_short_md.md)] 開發的應用程式或元件嘗試載入使用 [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] \(含\) 以後版本開發的組件，或當使用 [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] 或 [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] 開發的應用程式嘗試載入使用 [!INCLUDE[net_v40_short](../misc/includes/net_v40_short_md.md)] 開發的組件時，就會擲回此例外狀況。<xref:System.BadImageFormatException> 例外狀況可以以編譯階段的錯誤形式被報告，也可以以執行階段的例外狀況形式被擲回。 如需範例，請參閱 <xref:System.BadImageFormatException> 類別。  
  
 **請確定該檔案映像是有效的 Managed 組件或模組。**  
 當傳遞 Unmanaged 動態連結程式庫或可執行檔給 <xref:System.Reflection.Assembly.Load%2A> 方法來載入時，就會擲回此例外狀況。  
  
 如需詳細資訊，Visual Basic 使用者請參閱[Troubleshooting Interoperability](../Topic/Troubleshooting%20Interoperability%20\(Visual%20Basic\).md)。  
  
## 備註  
 反映 C\+\+ 可執行檔時可能會擲回這個例外狀況。 這個情況最可能的原因，是因為 C\+\+ 編譯器移除執行檔中的重新定位位置或 .Reloc 區段。 若要在 C\+\+ 執行檔中保留重新配置位址，請在連接時指定 **\/fixed:no**。  
  
 如需這個例外狀況的其他原因，請參閱 <xref:System.BadImageFormatException> 類別。  
  
## 請參閱  
 <xref:System.BadImageFormatException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)