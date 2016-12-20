---
title: "疑難排解例外狀況：System.Net.CookieException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "CookieException 類別"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Net.CookieException
將 Cookie 加入至 Cookie 容器時發生錯誤，便會擲回 <xref:System.Net.CookieException> 例外狀況。  
  
## 相關秘訣  
 **請確定 cookie 大小未超過 cookie 容器允許的最大值。**  
 嘗試將長度超過 <xref:System.Net.Cookie> 的 <xref:System.Net.CookieContainer.MaxCookieSize%2A> 加入至 <xref:System.Net.CookieContainer>，就會擲回這個例外狀況。 Cookie 大小的預設最大值為 4096 位元組。  
  
 **設定 Cookie 的 Name 屬性時，請確定該值不是 null 參考或空字串。**  
 使用 <xref:System.Net.Cookie.Name%2A> 類別的執行個體之前，必須先初始化 <xref:System.Net.Cookie> 屬性。 下列字元是保留字，無法用於這個屬性值中：等號 \(\=\)、逗號 \(,\)、新行 \(\\n\)、換行符號 \(\\r\)，和定位點 \(\\t\)。 第一個字元不能是貨幣符號 \($\) 字元。  
  
 **設定 Cookie 的 Port 屬性時，請確定該值是有效的，而且必須置於雙引號內。**  
 <xref:System.Net.Cookie.Port%2A> 屬性可以限制傳送 Cookie 的通訊埠。 預設值為沒有限制。 將這個屬性設定為空字串 \(""\) 會將通訊埠限制為 HTTP 回應中所使用的通訊埠。 否則該值必須是置於引號內的字串，其中包含以逗號區隔的通訊埠值。  
  
 **設定 Cookie 的 Value 屬性時，請確定該值不是 null。**  
 下列字元是保留字，無法用於這個屬性：分號 \(;\) 和逗號 \(,\)。  
  
## 請參閱  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)