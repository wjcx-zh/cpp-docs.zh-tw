---
title: "FxCopCmd 錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FxCopCmd 錯誤"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# FxCopCmd 錯誤
FxCopCmd 不會將所有的錯誤視為嚴重錯誤。  如果 FxCopCmd 擁有足夠的資訊可以執行部分分析，它就會執行分析並回報發生的錯誤。  錯誤碼是 32 位元的整數，其中包含對應至錯誤之數值的位元 \(Bitwise\) 組合。  
  
 下表描述 FxCopCmd 所傳回的錯誤碼：  
  
|錯誤|數值|  
|--------|--------|  
|沒有錯誤|0x0|  
|分析錯誤|0x1|  
|規則例外狀況 \(Exception\)|0x2|  
|專案載入錯誤|0x4|  
|組件 \(Assembly\) 載入錯誤|0x8|  
|規則程式庫載入錯誤|0x10|  
|匯入報告載入錯誤|0x20|  
|輸出錯誤|0x40|  
|命令列參數錯誤|0x80|  
|初始設定錯誤|0x100|  
|組件參考錯誤|0x200|  
|建置中斷錯誤|0x400|  
|未知的錯誤|0x1000000|  
  
 分析錯誤是針對嚴重錯誤所傳回的錯誤。  這種錯誤表示分析無法完成。  適用情況下，錯誤碼也會包含嚴重錯誤的根本原因。  下列情況會產生嚴重錯誤：  
  
-   由於輸入不足而無法執行分析。  
  
-   分析擲回 FxCopCmd 無法處理的例外狀況。  
  
-   找不到指定的專案或已損毀。  
  
-   未指定輸出選項或是無法寫入檔案。  
  
    > [!NOTE]
    >  FxCopCmd 傳回碼「組件參考錯誤」0x200 本身是警告而不是錯誤。  這個傳回碼表示發現遺漏的間接參考，但是 FxCopCmd 能夠處理這些參考。  這是個警告，表示可能某些分析結果會無法執行。  當「組件參考錯誤」傳回碼與任何其他傳回碼同時回傳時，請將它視為錯誤。  
  
## 請參閱  
 [程式碼分析應用程式錯誤](../Topic/Code%20Analysis%20Application%20Errors.md)