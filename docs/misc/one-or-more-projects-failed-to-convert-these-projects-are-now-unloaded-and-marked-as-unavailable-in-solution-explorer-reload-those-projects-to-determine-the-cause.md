---
title: "一或多個專案轉換失敗。 目前已卸載這些專案，並在 [方案總管] 中將其標記為無法使用。 請重新載入這些專案，以判斷問題來源。 | Microsoft Docs"
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
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 一或多個專案轉換失敗。 目前已卸載這些專案，並在 [方案總管] 中將其標記為無法使用。 請重新載入這些專案，以判斷問題來源。
您嘗試開啟方案，其中包含一或多個在舊版 Visual Studio 中建立的專案。 某些專案無法進行轉換，並將在 \[方案總管\] 中將其標記為 \(無法使用\)。 這些專案必須轉換為目前的格式，才能開啟及編輯您的方案，而且修復的專案可以在您電腦上安裝的 Visual Studio 版本中使用。  
  
### 若要回應這個訊息  
  
1.  按一下 \[是\] 以關閉對話方塊。  
  
     無法轉換的專案會在 \[方案總管\] 中標記為 **\(無法使用\)**。  
  
2.  重新載入無法轉換的專案。  
  
    1.  在方案總管中，選取使用中方案內標記為 **\(無法使用\)** 的每個專案。  
  
    2.  在 \[專案\] 功能表上，選擇 \[重新載入專案\]。  
  
3.  仔細檢閱顯示專案問題資訊的任何錯誤訊息。 可能的問題包括：  
  
    1.  專案為唯讀。 無法轉換唯讀專案。 只有具有編輯權限的使用者才能轉換這些專案。  
  
    2.  專案已獨佔地簽出給另一位使用者。 該使用者必須將專案重新簽入，您才能將其簽出。  
  
    3.  無法從網路伺服器簽出專案。 請確認網路狀況，然後再試一次。  
  
    4.  專案已損毀，而且必須重建。  
  
4.  當您嘗試重新載入標記為 **\(無法使用\)** 的專案時，請解決上述問題。  
  
5.  重新開啟並轉換這些專案。 轉換前，您可能需要建立專案檔的備份複本。  
  
    > [!NOTE]
    >  轉換特定專案類型時 \(例如 Visual C\+\+ 專案\)，舊的專案檔會以副檔名 .old 標示，並儲存在專案目錄中。  
  
 如果您隸屬於開發團隊，負責某個專案的所有人應該在其本機電腦上安裝相同版本的 Visual Studio。 為了確保您的專案維持在可供存取的狀態，請定期與您的團隊進行溝通。  
  
> [!CAUTION]
>  如果您方案中的專案儲存在原始程式碼控制之下，而且您想要重新簽入已轉換的專案，請先判斷是否有其他方案共用任何這類專案。 如果有未轉換的方案仍在使用已轉換的專案，請勿簽入這些專案。 這會中斷這些方案的內部相依性，導致無法正常開啟或建置這些方案。  
  
## 請參閱  
 [NIB：如何︰卸載和重新載入專案](http://msdn.microsoft.com/zh-tw/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/zh-tw/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)