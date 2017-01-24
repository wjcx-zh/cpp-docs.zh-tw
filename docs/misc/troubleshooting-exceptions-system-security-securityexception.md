---
title: "疑難排解例外狀況：System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException 類別"
  - "SecurityException 類別"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Security.SecurityException
偵測到安全性的錯誤時，就會擲回 <xref:System.Security.SecurityException> 例外狀況。  
  
## 相關秘訣  
 請透過屬性頁調整組件的存取權限等級。  
 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>。  
  
 將應用程式資料儲存在隔離儲存區。  
 隔離儲存區 \(Isolated Storage\) 為資料儲存機制，藉著定義標準化方式，將程式碼與儲存的資料產生關聯，以提供隔離和安全。 如需詳細資訊，請參閱[隔離儲存區](../Topic/Isolated%20Storage.md)。  
  
 如果使用 <xref:System.Windows.Forms.OpenFileDialog>，請使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法開啟或儲存檔案。  
 這可以讓應用程式在部分信任的情況下執行。  
  
 請確定應用程式是在本機電腦上讀取和寫入現有的事件日誌。  
 應用程式可能沒有足夠的存取權限在非本機電腦上建立日誌或進行寫入。  
  
 如果要呼叫 Unmanaged 程式庫，請使用對等的 Managed 程式庫。  
 Framework 中可能存有對等的 API。 如需詳細資訊，請參閱[Troubleshooting Interoperability](../Topic/Troubleshooting%20Interoperability%20\(Visual%20Basic\).md)。  
  
 請使用安全的視窗。  
 <xref:System.Security.Permissions.UIPermissionWindow> 列舉型別會指出程式碼允許使用的視窗類型。  
  
 允許使用者透過 <xref:System.Windows.Forms.PrintDialog> 元件進行列印。  
 這可以讓應用程式在部分信任的情況下執行。 如需詳細資訊，請參閱<xref:System.Windows.Forms.PrintDialog>。  
  
 請列印至預設印表機。  
 這可以讓應用程式在部分信任的情況下執行。 您可能會嘗試存取您沒有權限使用的印表機。  
  
 從部署它的同一部 Web 伺服器擷取資料。  
 這可以讓應用程式在部分信任的情況下執行。  
  
 部署 Office 方案時，請確定您已符合所有必要的安全性需求。  
 如需詳細資訊，請參閱[指定 Office 方案的安全性考量](../Topic/Specific%20Security%20Considerations%20for%20Office%20Solutions.md)。  
  
 如果實作自訂安全性物件的組件參考其他組件，請將參考的組件加入至完全信任組件清單中。  
 如需詳細資訊，請參閱[Caspol.exe \(Code Access Security Policy Tool\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md)。  
  
## 請參閱  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)