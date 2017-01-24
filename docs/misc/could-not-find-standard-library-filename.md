---
title: "找不到標準程式庫: &#39;&lt;檔案名稱&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40049"
  - "bc40049"
helpviewer_keywords: 
  - "BC40049"
ms.assetid: a292f97e-4852-4021-b300-7ab47beb95d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 找不到標準程式庫: &#39;&lt;檔案名稱&gt;&#39;
[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 找不到或無法開啟進行編譯和連結所需的其中一個標準 DLL 程式庫。  
  
 無法使用的程式庫極可能是 mscorlib.dll 或 microsoft.visualbasic.dll。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40049  
  
### 更正這個錯誤  
  
1.  請確認錯誤訊息中所指出的檔案存在於您執行 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 的硬碟上。 標準程式庫通常應該位於 \\WINNT\\Microsoft.NET\\Framework 或 \\WINDOWS\\Microsoft.NET\\Framework 的子目錄中。  
  
2.  請確認檔案和目錄都沒有防止 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 讀取的設定或屬性。  
  
3.  請確認檔名和副檔名的拼寫正確。 大小寫並不重要。  
  
4.  如果檔案的位置正確且可供存取，則它可能是在磁碟上損毀。 如果可能，請重新安裝 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]。  
  
5.  請記下確切的檔名和副檔名，然後連絡 Microsoft 產品支援服務。  
  
## 請參閱  
 [從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)   
 [How to: Invoke the Command\-Line Compiler](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)   
 [告訴我們](../Topic/Talk%20to%20Us.md)