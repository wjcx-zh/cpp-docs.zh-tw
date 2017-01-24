---
title: "檔案名稱中指定的檔案不是有效的 XML 檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 檔案名稱中指定的檔案不是有效的 XML 檔案
您提供的檔案名稱不是有效的 XML 檔案。 若要指定 XML 文件所允許的結構和內容，您可以使用文件類型定義 \(DTD\)、Microsoft XDR \(XML\-Data Reduced\) 結構描述或 XML 結構描述定義語言 \(XSD\) 結構描述。 建議使用 XSD 結構描述來指定 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 中的 XML 文法。  
  
> [!NOTE]
>  在某些舊版 Visual Studio 中，**XML 設計工具**是具類型資料集和 XML 結構描述的設計工具。**XML 設計工具**仍可用來建立及編輯 XML 結構描述檔案。 不過，在 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 中，用於建立及編輯具類型資料集的設計工具是 **DataSet 設計工具**。 如需詳細資訊，請參閱[建立和編輯具類型資料集](../Topic/Creating%20and%20Editing%20Typed%20Datasets.md)。  
  
### 更正這個錯誤  
  
-   確認您提供的檔案名稱正確。  
  
-   將您要檢查的 XML 檔案載入 **XML 設計工具**，以檢查指定的檔案是否包含有效的 XML。 從 \[XML\] 功能表按一下 \[驗證 XML\]。 \[工作清單\] 中會顯示錯誤。  
  
-   如果 XML 檔案有關聯的 XML 結構描述，請確認項目出現在定義的結構中，而且個別項目的內容符合結構描述中所指定的宣告資料類型。  
  
## 請參閱  
 <xref:System.Xml>   
 [如何：剖析檔案路徑](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)