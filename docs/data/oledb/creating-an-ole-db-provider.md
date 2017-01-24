---
title: "建立 OLE DB 提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者樣板, 建立提供者"
  - "OLE DB 提供者, 建立"
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 OLE DB 提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立 OLE DB 提供者的建議方式是，使用精靈來建立 ATL COM 專案和提供者，然後再使用 OLE DB 樣板來修改檔案。  當您自訂提供者時，可將不要的屬性設成註解，並加入選擇項介面。  
  
 基本的步驟如下所示  
  
1.  使用 ATL 專案精靈來建立基本的專案檔，並使用 ATL OLE DB 提供者精靈建立提供者 \(在 \[加入類別\] 的 \[Visual C\+\+\] 資料夾內選取 \[ATL OLE DB 提供者\]\)。  
  
2.  修改在 CMyProviderRS.h 中 `Execute` 方法的程式碼。  如需範例，請參閱[將字串讀入 OLE DB 提供者內](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。  
  
3.  編輯對應於 MyProviderDS.h、MyProviderSess.h 和 MyProviderRS.h 的屬性。  精靈會建立屬性對應，裡面包含提供者可能實作的所有屬性。  瀏覽一遍屬性對應，並將提供者不需要支援的屬性移除或設成註解。  
  
4.  更新 MyProviderRS.h 中的 PROVIDER\_COLUMN\_MAP。  如需範例，請參閱[將字串儲存於 OLE DB 提供者內](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。  
  
5.  當您要測試提供者時，可藉著在提供者列舉型別中尋找提供者來測試它。  如需可在列舉型別內尋找提供者的測試程式碼範例，請參閱 [CATDB](http://msdn.microsoft.com/zh-tw/003d516b-2bf6-444e-8be5-4ebaa0b66046)、和 [DBVIEWER](http://msdn.microsoft.com/zh-tw/07620f99-c347-4d09-9ebc-2459e8049832) 範例或[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)的範例。  
  
6.  加入任何其他您想要的介面。  如需範例，請參閱[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
    > [!NOTE]
    >  根據預設，精靈可產生與 OLE DB 層級 0 相容的程式碼。  若要確保應用程式可以相容於層級 0，請不要從程式碼中移除任何精靈產生的介面。  
  
## 請參閱  
 [CATDB](http://msdn.microsoft.com/zh-tw/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/zh-tw/07620f99-c347-4d09-9ebc-2459e8049832)