---
title: "Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyscatterassembly"
ms.assetid: 939519c7-741d-4e05-8b63-71e39fb426ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot copy multifile assembly &#39;assembly&#39; to directory &#39;directory&#39;. &lt;reason&gt;
多檔案組件會被複製到專案目錄的子目錄下，再從這裡執行。  例如，如果輸出路徑是 c:\\project1\\bin，且其中有一個包含 a.dll 和 b.dll 檔案的組件 Test \(其 `CopyLocal` 屬性為 `true`\)，那麼在複製完成之後檔案結構如下所示：  
  
```  
c:\project1\bin\Test  
   c:\project1\bin\Test\Test.dll   (main assembly)  
   c:\project1\bin\Test\a.dll       (file a.dll)  
   c:\project1\bin\Test\b.dll       (file b.dll)  
```  
  
 如果無法在磁碟上建立目錄 c:\\project1\\bin\\Test，專案系統就會出現這個錯誤。  
  
 這個錯誤表示磁碟空間不足或達到路徑長度的 MAX\_PATH 限制。  
  
 **若要更正這個錯誤**  
  
-   檢查磁碟空間。  
  
-   嘗試將專案移動到路徑長度小於目前專案資料夾路徑長度的資料夾中。  
  
-   將輸出目錄變更為具有較短絕對路徑長度的資料夾 \(僅適用於用戶端專案\)。  
  
## 請參閱  
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)   
 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-tw/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)