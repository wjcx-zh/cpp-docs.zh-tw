---
title: "無法將檔案 &#39;filename&#39; 複製至執行目錄。 &lt;原因&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_to_run_dir"
ms.assetid: 80474e62-7cef-48e9-a7c0-820345d5b591
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法將檔案 &#39;filename&#39; 複製至執行目錄。 &lt;原因&gt;
這個錯誤顯示於：  
  
-   將 `CopyLocal` 屬性 \(從方案總管中選取參考時，請參閱 \[屬性\] 視窗\) 設定為 `true` 的參考無法複製到專案執行目錄。  
  
-   將 `CopyLocal` 屬性設定為 `true` 的參考相依性無法複製到專案執行目錄。  
  
-   需要在本機複製的任何其他檔案，都無法複製到專案執行目錄。  
  
 大多數情況下，錯誤訊息結尾引述的 `reason` 會報告有其他處理序正在使用檔案。 可能是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 內的其他物件鎖定了這個檔案。  
  
 將專案建置至相同的輸出目錄中可能發生了問題。 如果是這種情況，請在兩個不同的目錄建立專案。 建置至不同的目錄中時，專案系統會將所有相依組件複製到專案的輸出目錄。  
  
 將任何工作中專案的輸出加入為工具箱項目，會導致受管理的設計工具鎖定參考。  
  
 如果輸出目前正在執行，專案系統就不能更新輸出目錄。  
  
 **更正這個錯誤**  
  
-   檢查電腦的可用磁碟空間  
  
-   檢查是否到達檔案系統加諸的 MAX\_PATH 限制  
  
     這種情況不會防止建置專案。 不過，它可能會造成專案無法正常運作，因為這則警告指出，無法正確更新參考組件的私用複本。 雖然專案或許可以執行，但在執行特定程式碼路徑時，可能會收到類型載入例外狀況或其他意外行為。  
  
## 請參閱  
 [NIB：如何：設定參考的 &#91;複製本機&#93; 屬性](http://msdn.microsoft.com/zh-tw/dfe2ba13-f27f-4356-a481-ea67d5acacbd)