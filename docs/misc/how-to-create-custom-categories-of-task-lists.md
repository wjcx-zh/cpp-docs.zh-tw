---
title: "如何：建立工作清單的自訂分類 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工作清單, 自訂分類"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 如何：建立工作清單的自訂分類
自訂工作目錄，提供控制如何在顯示任務的**工作清單**視窗。  
  
 實作自訂的類別的任務，原因如下：  
  
-   您想要控制您的類別目錄會顯示的位置 \(排序\)，在 \[類別\] 清單中。  
  
-   您有幾個的子類別的 \[您想要在一個分類排序，而不排序它們之間的其他工作的工作。  
  
-   您想要建立自訂檢視，其中顯示您的工作。  
  
    > [!NOTE]
    >  一種效果類似的自訂類別而不實際實施，則為自訂類別。  比方說，您可以顯示為點陣圖，類別或子類別，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A>。  工作提供者提供的清單，然後每項任務提供索引插入清單。  
  
 若要建立自訂的類別目錄中**工作清單**，它與登錄 **工作清單**藉由使用下列程序。  
  
### 若要註冊自訂工作清單分類  
  
-   呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A>要註冊一個自訂的分類，工作清單。  
  
     每個自訂類別必須有它自己的 GUID，這個值`guidCat`參數。  在`dwSortOrder`參數，提供您想要此類別來排序 \(當 \[依類別排序清單\) 的位置的位置。  接著這個方法會傳回實際的排序位置較大的一份分類清單中的自訂分類。  
  
     排序順序的內建工作類別\] 中定義的<xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY>列舉型別，如下表中。  
  
    |分類|值|描述|  
    |--------|-------|--------|  
    |CAT\_ALL|1|真正的類別。  用來允許工作清單檢視以顯示所有工作\]，在**工作清單**。|  
    |CAT\_BUILDCOMPILE|10|建置錯誤、 警告與可能的部署錯誤。|  
    |CAT\_COMMENTS|20|特殊的註解，例如"TODO"，所產生的工作"復原"侵入"。|  
    |CAT\_CODESENSE|30|當您輸入的原始程式碼所產生的錯誤。|  
    |CAT\_SHORTCUTS|40|程式碼的捷徑。|  
    |CAT\_USER|50|使用者輸入的工作。|  
    |CAT\_MISC|60|VSPackages 可能會想要加入的其他工作**工作清單**。|  
    |CAT\_HTML|70|有關開發 Web 網頁的工作。|  
  
     比方說，若要包含的 CAT\_CODESENSE 和 CAT\_SHORTCUTS 之間的類別，您可能會傳入值 31 的排序順序。  不過，因為另一個自訂工作提供者類別，可能已經使用 31 數值**工作清單**會將您下一步的空插槽的任務類別的指派。  這個值會傳遞至您在`pCat`參數。  
  
### 若要移除註冊自訂工作清單類別  
  
-   呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A>取消註冊您的自訂類別。  
  
## 請參閱  
 [建立自訂工作清單檢視](../misc/creating-custom-task-list-views.md)