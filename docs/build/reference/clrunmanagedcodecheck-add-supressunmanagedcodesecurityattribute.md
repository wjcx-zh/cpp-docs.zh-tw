---
title: "/CLRUNMANAGEDCODECHECK (加入 SupressUnmanagedCodeSecurityAttribute) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRUNMANAGEDCODECHECK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRUNMANAGEDCODECHECK 連結器選項"
  - "-CLRUNMANAGEDCODECHECK 連結器選項"
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRUNMANAGEDCODECHECK (加入 SupressUnmanagedCodeSecurityAttribute)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/CLRUNMANAGEDCODECHECK** 會指定連結器是否將 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 套用至從 Managed 程式碼對原生 DLL 之連結器所產生的 `PInvoke` 呼叫。  
  
## 語法  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## 備註  
 根據預設，連結器會將 SuppressUnmanagedCodeSecurityAttribute 套用至連結器產生的 `PInvoke` 呼叫。  當 **\/CLRUNMANAGEDCODECHECK** 為作用中時，則不會套用 SuppressUnmanagedCodeSecurityAttribute。  
  
 連結器只將屬性加入至使用 **\/clr** 或 **\/clr:pure** 編譯的物件中。  連結器不會在使用 **\/clr:safe** 編譯的物件中產生 `PInvoke` 呼叫。  如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 連結器找不到 Managed 符號，以滿足來自 Managed 呼叫端的參考，但找得到原生符號，以滿足該參考時，就會由連結器產生 `PInvoke` 呼叫。  如需 `PInvoke` 的詳細資訊，請參閱 [從 Managed 程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)。  
  
 請注意，如果您是在程式碼中使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>，應該明確地設定 **\/CLRUNMANAGEDCODECHECK**。  如果影像中同時包含 SuppressUnmanagedCodeSecurity 和 AllowPartiallyTrustedCallers 兩個屬性，可能會成為潛在的安全性漏洞。  
  
 如需關於使用 SuppressUnmanagedCodeSecurityAttribute 之隱含意義的詳細資訊，請參閱[Security Optimizations](http://msdn.microsoft.com/zh-tw/cf255069-d85d-4de3-914a-e4625215a7c0)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**進階**\] 屬性頁。  
  
5.  修改 \[**CLR Unmanaged 程式碼檢查**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)