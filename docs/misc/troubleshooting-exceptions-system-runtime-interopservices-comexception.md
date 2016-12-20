---
title: "疑難排解例外狀況：System.Runtime.InteropServices.COMException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHCOM"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "COMException 類別"
ms.assetid: 14b6de51-e039-4db7-9321-06c9e16e328a
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Runtime.InteropServices.COMException
COM 方法呼叫傳回無法辨認的 HRESULT 時，就會擲回 <xref:System.Runtime.InteropServices.COMException> 例外狀況。  
  
## 相關秘訣  
 **請檢查該例外狀況的 ErrorCode 屬性，以判斷 COM 物件所傳回的 HRESULT**  
 當執行階段遇到不熟悉的 HRESULT 時，就會擲回包含公用 <xref:System.Runtime.InteropServices.COMException> 屬性的 `ErrorCode` 例外狀況，這個屬性包含了該呼叫所傳回的 HRESULT。 如果執行階段能取得錯誤訊息，該訊息則會被傳回呼叫端。 但是，如果 COM 組件開發人員無法納入錯誤訊息，執行階段則會傳回八位元的 HRESULT 取代訊息字串。 取得 HRESULT 可讓呼叫端判斷例外狀況發生的原因。 如需詳細資訊，請參閱[如何：對應 HRESULT 和例外狀況](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)。  
  
 **停用裝載處理序。**  
 COM 是用於進行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 和裝載處理序之間的溝通。 因為它會在程式碼執行之前使用，因此對 `CoInitializeSecurity` 呼叫就會擲回這個例外狀況。  
  
### 備註  
 Common Language Runtime \(CLR\) 會將已知的 HRESULTS 轉換為 .NET 例外狀況，讓 COM 物件能將有意義的錯誤訊息傳回 Managed 用戶端。 HRESULT 與例外狀況的對應也能以另一種方向運作，將特定的 HRESULTS 傳回 Unmanaged 用戶端。  
  
 將晚期繫結的參數傳遞至 Microsoft Office 物件的方法時，這個物件若是 COM 物件，則可能會擲回 <xref:System.Runtime.InteropServices.COMException> 例外狀況。 晚期繫結器 \(Binder\) 會假設這個方法呼叫包含 `ByRef` 參數，並假設您傳遞的屬性具 有 `Set` 存取子。 如果屬性未具有此存取子，[!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 就會產生 <xref:System.MissingMethodException> 例外狀況 \(HRESULT CORE\_E\_MISSINGMETHOD\)。 若要解決這個行為，請使用早期繫結的物件，或傳遞變數而不要傳遞物件的屬性。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.COMException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [處理 COM Interop 例外狀況](../Topic/Handling%20COM%20Interop%20Exceptions.md)