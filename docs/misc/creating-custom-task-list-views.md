---
title: "建立自訂工作清單檢視 | Microsoft Docs"
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
  - "工作清單, 自訂檢視"
ms.assetid: c25f8f5d-55a1-4b5e-b617-3d1140bcb98a
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 建立自訂工作清單檢視
藉由建立自訂工作清單檢視，您可以在 Visual Studio 中顯示自訂工作清單。  
  
 使用登錄來建立自訂檢視，並使這些規格：  
  
-   資料行  
  
-   資料行的排序順序  
  
-   預設的排序順序  
  
-   工作所要類別顯示  
  
 您可以顯示一個自訂類別，或指定多個類別的 CAT\_ALL。  您也可以建立自訂文字欄位包含任何文字。  不過，您無法自訂的文字資料行進行排序。  
  
 下表顯示自訂工作清單檢視的登錄格式。  
  
 在每個資料表，  *VS Reg 根*等於 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\8.0\\。  資料表會提供指令碼項目與每個登錄陳述式的額外資訊。  
  
 *VS Reg 根*\\TaskList\\Views\\*GUID*  
  
|名稱|型別|Range|描述|  
|--------|--------|-----------|--------|  
|名稱|REG\_SZ|文字|\[檢視\] 或 \[\# xxx 字串名稱。<br /><br /> 這個名稱可以是一般的字串，如 \[我的自訂檢視\] 或在封裝中 \(\# xxx\) 的資源字串。|  
|封裝|REG\_SZ|文字|\[選擇\]GUID 的字串表示。  這是必要的如果某些字串的資源字串 \(\# xxx\) ； 否則，它會被忽略。|  
  
 *VS Reg 根*\\TaskList\\Views\\*GUID*\\Columns\\*編號*  
  
> [!NOTE]
>  *數字*是以 1 起始的順序在檢視中的資料行 \(其中 1 是最左邊的欄\)。  更多的資料行的遞增*編號*。  
  
|名稱|型別|Range|描述|  
|--------|--------|-----------|--------|  
|欄位|REG\_DWORD||A <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD>也就是資料行的欄位。|  
|Width|REG\_DWORD||選擇項。  資料行的寬度 \(以像素為單位\)。  如果資料行不是可調大小的則會忽略這個參數。|  
|索引|REG\_DWORD||選擇項。  如果欄位是 FLD\_CUSTOM，這會是自訂的資料行索引。|  
|名稱|REG\_SZ|文字|如果欄位是 FLD\_CUSTOM，這是自訂的資料行名稱。<br /><br /> 名稱也可以是 \# xxx 格式的資源字串。|  
|篩選條件|REG\_SZ 或呼叫完成||不論是哪一 DWORD 具有內建的 VSTASKCATEGORY 或字串，表示自訂類別的 GUID。|  
  
 *VS Reg 根*\\TaskList\\Views\\*GUID*\\Sort\\*編號*  
  
> [!NOTE]
>  *數字*識別排序鍵。  例如，對於主要排序鍵， *編號*等於 1。  第二個排序鍵， *編號*等於 2，依此類推。  
  
|名稱|型別|Range|描述|  
|--------|--------|-----------|--------|  
|欄位|REG\_DWORD||A <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD>也就是資料行的欄位。|  
|索引|REG\_DWORD||選擇項。  如果欄位是 FLD\_CUSTOM，這會是自訂的資料行索引。|  
  
 若要實作自訂的資料行，您必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2>介面，在您的工作項目，而且您必須實作該介面上的下列方法：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.get_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.put_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.IsCustomColumnReadOnly%2A>  
  
 視需要在查詢工作清單您<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2>實作，藉由使用自訂的資料行特定的檢視中，所表示的數字*一些 guid*。  如果您的工作有適當的資訊，該資料行的相關檢視中，您提供資訊以該資料行，並指定所指定文字是否為唯讀。  
  
## 請參閱  
 [如何：建立工作清單的自訂分類](../misc/how-to-create-custom-categories-of-task-lists.md)