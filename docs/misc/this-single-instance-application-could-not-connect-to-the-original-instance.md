---
title: "此單一執行個體應用程式無法連接到原始執行個體 | Microsoft Docs"
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
  - "vbrAppModel_SingleInstanceCantConnect"
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此單一執行個體應用程式無法連接到原始執行個體
此單一執行個體應用程式無法連接到原始執行個體。 此問題的部分可能原因如下：  
  
-   原始執行個體停止回應。  
  
-   應用程式沒有建立核心物件的權限。 如需有關核心物件的詳細資訊，請參閱 [Mutexes](../Topic/Mutexes.md)。  
  
     核心物件的主檔名 \(Base Name\) 是由連接組件的 GUID、主要版本號碼，以及次要版本號碼所組成。 例如，基底名稱可能是 `3639f15d-9547-43da-8145-60da347829915.1`。  
  
### 在開發應用程式時更正這個錯誤  
  
1.  檢查應用程式並未進入沒有回應的狀態。  
  
2.  檢查應用程式有足夠的權限可建立核心物件。  
  
3.  重新啟動應用程式的原始執行個體。  
  
4.  重新啟動電腦，以針對連接到原始執行個體應用程式所需的資源，清除可能正在使用它的任何處理序。  
  
5.  記下錯誤發生時的情況，並致電 Microsoft 產品支援服務。  
  
## 請參閱  
 [NIB: 如何：指定應用程式的執行個體行為 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [偵錯工具基礎](../Topic/Debugger%20Basics.md)   
 [PAVEOVER 產品支援和協助工具](http://msdn.microsoft.com/zh-tw/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)