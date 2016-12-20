---
title: "疑難排解例外狀況：System.FormatException | Microsoft Docs"
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
  - "FormatException 類別"
ms.assetid: b2a4f55e-da87-4915-a053-59eb1595993d
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.FormatException
當引數格式不符合剖析或格式化類型之方法的參數規格時，此方法會擲回 <xref:System.FormatException> 例外狀況。  
  
## 本文內容  
  
## 造成格式例外狀況  
  
### 格式化  
 *「格式化」*\(Formatting\) 是將類別、結構或列舉值的執行個體轉換成其字串表示的過程，通常是為了將結果字串向使用者顯示，或是為了用於儲存物件的狀態。  
  
 例如，<xref:System.Int32.ToString%28System.String%29?displayProperty=fullName> 接受識別標準或自訂*「格式字串」*\(format string\) 的字串參數，並傳回數字的字串表示。 如果格式字串是無效或不受支援，這個方法會擲回 <xref:System.FormatException>。  
  
### 複合格式  
 *「複合格式化」*\(Composite formatting\) 接受物件清單和複合格式字串做為輸入。 複合格式字串是由混合索引替代符號 \(Placeholder\) 的固定文字所組成 \(這些符號稱為對應至清單內物件的格式項目\)。 格式作業產生的結果字串是由原始固定文字所組成，這些固定文字混合了清單中代表物件的字串。  
  
 <xref:System.String.Format%2A?displayProperty=fullName> 和 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 是執行複合格式化的方法範例。 如果格式字串無效，或格式項目的索引小於零，或大於或等於引數數目，使用複合格式化的方法會擲回 <xref:System.FormatException>。  
  
### 剖析  
 *「剖析」*\(Parsing\) 是將代表 .NET Framework 基底類型的字串轉換為該基底類型的過程。 例如，剖析作業用來將字串轉換為浮點數或日期和時間值。  
  
 例如，<xref:System.Int32.Parse%28System.String%29?displayProperty=fullName><xref:System.DateTime.Parse%2A> 將日期和時間的字串表示，藉由使用 <xref:System.IformatProvider> 參數中指定的文化特性格式資訊，轉換為其 <xref:System.DateTime> 對等項。 如果字串不是正確的格式，就會擲回 <xref:System.FormatException>。  
  
## 避免 FormatExceptions  
 <xref:System.FormatException> 類別參考文章包含 <xref:System.FormatException> 錯誤的常見原因和解決方案。  
  
 MSDN Library 的[格式化類型](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)和[剖析字串](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md)章節包含正確格式化和剖析類型的相關資訊。  
  
 **複合格式化**  
  
 [複合格式](../Topic/Composite%20Formatting.md)  
  
 **數值類型**  
  
|||  
|-|-|  
|[標準數值格式字串](../Topic/Standard%20Numeric%20Format%20Strings.md)|[自訂數值格式字串](../Topic/Custom%20Numeric%20Format%20Strings.md)|  
|[剖析數值字串](../Topic/Parsing%20Numeric%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **日期和時間及 Timespan 類型**  
  
|||  
|-|-|  
|[標準日期和時間格式字串](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)|[自訂日期和時間格式字串](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)|  
|[標準 TimeSpan 格式字串](../Topic/Standard%20TimeSpan%20Format%20Strings.md)|[自訂 TimeSpan 格式字串](../Topic/Custom%20TimeSpan%20Format%20Strings.md)|  
|[剖析日期和時間字串](../Topic/Parsing%20Date%20and%20Time%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **其他類型**  
  
|||  
|-|-|  
|[列舉類型格式字串](../Topic/Enumeration%20Format%20Strings.md)|[剖析其他字串](../Topic/Parsing%20Other%20Strings%20in%20the%20.NET%20Framework.md)|