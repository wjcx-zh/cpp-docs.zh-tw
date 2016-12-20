---
title: "這些專案組態都已過期：&lt;組態&gt;。 要建置嗎? | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 這些專案組態都已過期：&lt;組態&gt;。 要建置嗎?
您正在編輯 Visual Studio 專案或在 \[方案總管\] 中選取了一個專案，而且已選擇 \[啟動\] \(F5\) 專案或 \[啟動但不偵錯\] \(CTRL\+F5\)。 一或多個專案可在不重建的情況下進行偵錯，即使該專案自上次建置後已修改亦然。  
  
 整合式開發環境 \(IDE\) 正在詢問是否重建可在不重建的情況下進行偵錯的專案。  
  
### 若要回應這個訊息  
  
-   選取訊息底部的其中一個按鈕。 可選的按鈕有：  
  
|詞彙|定義|  
|--------|--------|  
|**是**|您將重建過期的專案。 這表示：<br /><br /> -   如果尚未建置專案，就會建置專案。<br />-   如果專案自上次建置後已修改，就會重建專案。<br />-   針對專案進行偵錯，或啟動但不偵錯。|  
|**否**|您只會重建必須在偵錯前重建的過期專案。 這表示：<br /><br /> -   如果專案可在不重建的情況下進行偵錯 \(例如 Visual C\+\+ MFC 應用程式專案\)，就不會重建專案。<br />-   如果專案必須在偵錯前重建 \(例如 Visual Basic 專案\)，就會重建專案。<br />-   針對專案進行偵錯，或啟動但不偵錯。|  
|**取消**|停止目前的作業 不會建置、啟動或偵錯任何專案。|  
  
## 請參閱  
 [&#91;組態管理員&#93; 對話方塊](http://msdn.microsoft.com/zh-tw/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [如何：建立方案和專案組建組態](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [如何：建立和移除專案相依性](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-tw/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/zh-tw/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)   
 [了解組建組態](../Topic/Understanding%20Build%20Configurations.md)   
 [NIB︰以專案作為容器](http://msdn.microsoft.com/zh-tw/87d40f63-f487-4767-8963-64beec27ba1b)   
 [NIB：專案中的項目管理](http://msdn.microsoft.com/zh-tw/762e606b-7f44-4b66-97a1-e30a703654a0)