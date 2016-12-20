---
title: "組件 &#39;&lt;檔案路徑1&gt;&#39; 參考組件 &#39;&lt;組件識別&gt;&#39;，所參考的組件在 &#39;&lt;檔案路徑2&gt;&#39; (由專案 &#39;&lt;專案名稱1&gt;&#39; 參考) 和 &#39;&lt;檔案路徑3&gt;&#39; (由專案 &#39;&lt;專案名稱2&gt;&#39; 參考) 之間模稜兩可 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42204"
  - "vbc42204"
helpviewer_keywords: 
  - "BC42204"
ms.assetid: b0c3d2b6-2776-4981-b79e-2e36f03d4123
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 組件 &#39;&lt;檔案路徑1&gt;&#39; 參考組件 &#39;&lt;組件識別&gt;&#39;，所參考的組件在 &#39;&lt;檔案路徑2&gt;&#39; (由專案 &#39;&lt;專案名稱1&gt;&#39; 參考) 和 &#39;&lt;檔案路徑3&gt;&#39; (由專案 &#39;&lt;專案名稱2&gt;&#39; 參考) 之間模稜兩可
組件 '\<檔案路徑1\>' 參考組件 '\<組件識別\>'，所參考的組件在 '\<檔案路徑2\>' \(由專案 '\<專案名稱1\>' 參考\) 和 '\<檔案路徑3\>' \(由專案 '\<專案名稱2\>' 參考\) 之間模稜兩可， 將使用 '\<檔案路徑2\>'。 如果兩個組件完全相同，請將參考變更到相同的位置。  
  
 組件存取了另一個組件中的類型，並具有多個檔案參考。  
  
 編譯器無法保證在不同位置的檔案具有同一個組件的相同版本。 因此，檔案參考會模稜兩可，而且編譯器必須選取其中一個。  
  
 *「組件識別」*\(assembly identity\) 包含組件的名稱、版本、公開金鑰 \(如果有\) 和文化特性。 這是可唯一識別組件的資訊。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42204  
  
### 更正這個錯誤  
  
1.  決定哪個檔案最適合代表組件。 您可以在適合的情況下使用準則，例如最新版本、檔案的存取範圍及更新的可能性。  
  
2.  將所有檔案參考變更到這個組件，以便其針對您選擇的檔案使用相同的檔案路徑。  
  
## 請參閱  
 [不在組建中：組件](http://msdn.microsoft.com/zh-tw/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [Common Language Runtime 中的組件](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [組件的優點](../Topic/Assembly%20Benefits.md)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：管理參考](http://msdn.microsoft.com/zh-tw/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)