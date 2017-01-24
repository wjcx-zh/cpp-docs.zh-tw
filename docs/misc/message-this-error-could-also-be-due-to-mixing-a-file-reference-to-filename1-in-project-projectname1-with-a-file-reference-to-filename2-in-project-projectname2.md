---
title: "&lt;訊息&gt; 這個錯誤也可能是因為混用了專案 &#39;&lt;專案名稱1&gt;&#39; 的 &#39;&lt;檔案名稱1&gt;&#39; 檔案參考和專案 &#39;&lt;專案名稱2&gt;&#39; 的 &#39;&lt;檔案名稱2&gt;&#39; 檔案參考 | Microsoft Docs"
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
  - "bc30970"
  - "vbc30970"
helpviewer_keywords: 
  - "BC30970"
ms.assetid: 81cc4f7b-cc16-46cc-9a49-74980300e158
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;訊息&gt; 這個錯誤也可能是因為混用了專案 &#39;&lt;專案名稱1&gt;&#39; 的 &#39;&lt;檔案名稱1&gt;&#39; 檔案參考和專案 &#39;&lt;專案名稱2&gt;&#39; 的 &#39;&lt;檔案名稱2&gt;&#39; 檔案參考
\<訊息\> 這個錯誤也可能是因為混用了專案 '\<專案名稱1\>' 的 '\<檔案路徑名稱1\>' 檔案參考和專案 '\<專案名稱2\>' 的 '\<檔案路徑名稱2\>' 檔案參考  如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。  
  
 您專案中的程式碼會存取另一個專案的成員，但您的解決方案組態不允許 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器解析參考。  
  
 若要存取另一個組件中所定義的類型，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤識別碼：**BC30970  
  
### 更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。  
  
## 請參閱  
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)