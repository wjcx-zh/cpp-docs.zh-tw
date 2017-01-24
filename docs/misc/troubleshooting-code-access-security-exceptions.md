---
title: "疑難排解程式碼存取安全性之例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CodeAccessPermission 類別"
  - "CodeAccessSecurityException 類別"
  - "程式碼存取安全性, 疑難排解"
  - "安全性 [偵錯工具], 程式碼存取安全性疑難排解"
  - "程式碼存取安全性疑難排解"
ms.assetid: ca368d3b-f6d0-4c89-af59-d94f343fca35
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解程式碼存取安全性之例外狀況
權限會控制程式碼允許和不允許進行哪些作業。 在執行應用程式時，執行階段便會授與一組權限。 如果應用程式具有足夠的權限，就會正確地執行，否則，會發生安全性例外狀況。  
  
 程式碼所獲得的權限，取決於應用程式的啟動位置 \(例如，網際網路、內部網路或本機電腦\)，以及執行應用程式所在電腦的安全性設定。 由於這些設定可能會依每部電腦而有所不同，因此，您不能總是預期程式碼是否會得到充分的權限。  
  
 如果本機電腦上的安全性原則允許所要求的權限，便能夠確保程式碼可以執行。 如果沒有要求必要的權限，就必須承擔無法執行程式碼的風險。 如需程式碼存取權限和要求這些權限的詳細資訊，請參閱[程式碼存取權限](http://msdn.microsoft.com/zh-tw/e5ae402f-6dda-4732-bbe8-77296630f675)或[NIB：要求權限](http://msdn.microsoft.com/zh-tw/0447c49d-8cba-45e4-862c-ff0b59bebdc2)。 如需 `Try...Catch` 區塊的詳細資訊，請參閱 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)。  
  
 必要時，[!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 應用程式可以利用 \[應用程式設計工具\] 中的 \[安全性\] 頁面，來要求其他權限。 如需詳細資訊，請參閱[如何：設定 ClickOnce 應用程式的自訂使用權限](../Topic/How%20to:%20Set%20Custom%20Permissions%20for%20a%20ClickOnce%20Application.md)。  
  
 發生程式碼存取安全性例外狀況的可能原因包括：  
  
-   **剪貼簿：**由於 \[剪貼簿\] 可能含有敏感資訊，因此，以程式設計方式從 \[剪貼簿\] 貼上是受到限制的 Managed 程式碼功能。  
  
-   **登錄或檔案系統存取：**對本機檔案系統的存取會受到限制。 如果要存取與組件一起部署的檔案或資源，請使用程式碼 `Assembly.GetExecutingAssembly.Location` 以取得組件的路徑。  
  
-   **網路存取：**確定組件使用的通訊協定，與當初載入組件時所使用的通訊協定相同。 一般而言，只允許對屬於組件來源的 URL 使用網路通訊。  
  
-   **列印：**在網際網路區域中執行的軟體只能使用通用對話方塊來進行列印。只有在使用通用對話方塊允許使用者選取印表機的情況下，才會限制只能使用預設的印表機。  
  
-   **序列化：**以完全信任執行的程式碼，從任意資料重建物件的能力會受到限制。 如果要進行 XML 序列化，技術上 `XmlSerializer` 類型必須能由部分信任的程式碼使用。 如需 `XmlSerializer` 類型的詳細資訊，請參閱 [XmlSerializer 類別](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)。  
  
-   **反映。**部分信任的程式碼受到限制，無法使用執行階段的許多反映相關功能。  
  
## 測試程式碼以判斷是否會擲回程式碼存取安全性例外狀況  
 如果您擁有的程式碼區塊可能會擲回 `CodeAccessSecurityException`，請使用 `Try...Catch` 區塊，允許程式碼在能夠執行時順利執行，並且在無法執行時利用其他方法解決失敗的問題。  
  
 有時候，您可能想要設計應用程式，以便根據主機系統所授與的權限，來調整應用程式的行為。 例如，如果應用程式沒有列印權限，您可能想要停用功能表上的列印命令。  
  
 若要針對這點進行測試，您可以建立 `CodeAccessPermission` 衍生類別的執行個體，例如 `FileIOPermission`。 然後，您可以針對 `Try...Catch` 區塊內部的權限，執行 `Demand` 方法。 如果擲回例外狀況，表示您的組件不具有該權限。  
  
 下列範例會執行或建立 `EventLogPermission`，並在 `Try...Catch` 區塊內執行它的 `Demand` 方法，以判斷 `Demand` 是否成功，藉此測試組件是否具有 `EventLogPermission` 權限。  
  
```  
Try Dim MyPermission As New EventLogPermission MyPermission.Demand() MsgBox(MyPermission.ToString()) Catch ex As Exception MsgBox("Assembly lacks EventLogPermission.") End Try  
```  
  
## 請參閱  
 [程式碼存取權限](http://msdn.microsoft.com/zh-tw/e5ae402f-6dda-4732-bbe8-77296630f675)   
 [NIB：要求權限](http://msdn.microsoft.com/zh-tw/0447c49d-8cba-45e4-862c-ff0b59bebdc2)   
 [Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)